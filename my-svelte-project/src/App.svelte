<script>
    let newItem = '';
	
    let todoList = [{text: 'Я Лена', status: true},
                    {text: 'это мой todolist', status: false},
                    {text: 'привет', status: false}];
	
	function addToList() {
		todoList = [...todoList, {text: newItem, status: false}];
		newItem = '';
	}
	function checkedAction(status,index){
		console.log(index,status);
		if(todoList[index].status == true) {
			todoList[index].status = false;
		}
		else	{
			todoList[index].status = true;

		}

	}

	
	function removeFromList(index) {
		todoList.splice(index, 1)
		todoList = todoList;
    }
</script>
<div class="container-fluid">
	<div id="myDIV" class="header pt-5">
		<div class="row justify-content-center">
			<div class="col-lg-5 px-0">
				<div class="logo"><img src="logo.png" alt="" class="w-100"></div>
				<div class="add mt-5">
					<input bind:value={newItem} id="myInput" type="text" placeholder="new todo item..">
					
					<span on:click={addToList} class="add-button">+</span>

				</div>
			</div>
		</div>
	</div>
</div>

<div class="container-fluid">
	<div class="row justify-content-center">
		<div class="col-lg-5 px-0">
			<ul id="myUL">
				{#each todoList as item, index}
		          <li class:checked={item.status} on:click={checkedAction(item.status,index)}>{item.text} 
					<span on:click={() => removeFromList(index)} class="close">&#215;</span> </li>
				{/each}
			</ul>
		</div>
	</div>
</div>
<br/>

<style> 
	.checked {
        text-decoration: line-through;
    }
</style> 