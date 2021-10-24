<script>
	import Header from "./components/Header.svelte";
	import Dashboard from './components/Dashboard.svelte'
  import  {v4} from 'uuid'
  import { darkMode } from './store/store.js'

	let notes = [{
        id: "",
        title: 'Hacer Ejercicios',
        text: 'Rutina pecho',
        color: '#ddffc2',
    },{
		id: "1",
        title: 'Comer 3 veces',
        text: 'Comida variada',
        color: '#ffc2c2',
	}]

  $:count = notes.length

  let copyNotes = [... notes]

  const generateColor = () => {
    const colors = ['#ddffc2','#ffc2c2','#ffeac2','#c2ffd3', '#c2ffedc','linear-gradient(#64cce6, #9198e5)']
    const index = Math.floor(Math.random() * colors.length)

    return colors[index];
  }

  const handleNew = () => {
    const color = generateColor()
    const note = {
      id: v4(),
      title: '',
      text: '',
      color: color
    }
    notes = [note, ...notes]
    copyNotes = [...notes]
  }

  const handleUpdate = e => {
    const n = e.detail
    const i = notes.findIndex(e => e.id === n.id)

    notes[i] = n
    copyNotes = [...notes]
  }

  const handleColor = e => {

    const index = notes.findIndex(n => n.id === e.detail.id)
    notes[index].color = generateColor()
    copyNotes = [... notes]

  }

  const handleRemove = e => {

    const newNotes = notes.filter(n => n.id !== e.detail.id) 
    notes = [...newNotes]
    copyNotes = [...notes]
  }

  const handleSearch = (e) => {
    const _n = e.target.value
    console.log(_n)

    if(_n === ''){
      copyNotes = [...notes]
      return false
    }
    
    const result = notes.filter(n => {
        const title = n.title.toLowerCase()
        const text = n.text.toLowerCase()

        return title.indexOf(_n) > -1 || text.indexOf(_n) > -1
    })
    copyNotes = [...result]
    

  }

</script>

<main class={$darkMode ? 'darkMode' : ''}>
  <Header on:input={handleSearch}/>
  <div class="count">Total notas: {count}</div>
	<Dashboard 
  bind:notes={copyNotes} 
  on:color={handleColor}
  on:remove={handleRemove}
  on:click={handleNew}
  on:update={handleUpdate}/>
</main>

<style>
  :global(main.darkMode){
    background-color: rgb(29, 28, 28);
    color: white;
    padding: 0;
    margin: 0;
    height: 100%;
  }
	.count{
    text-align: right;
    padding: 10px 0;
    box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
  }
 
</style>