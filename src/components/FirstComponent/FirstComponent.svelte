<script>
    
    export var prop; // to expoert a prop 
    const item = 10;
	const title = "Hello world Svelte";
    var num = 0;
    const counterNumber = () => {
        return (num++);
    };

    

    var spanGroup = `<span></span>`;
    

    console.log("prop",prop);
</script>

<div >
    <h1>{title}</h1>
    <div>
       <button on:click={counterNumber}>
        click me {num}
       </button>
    </div>
    <slot>
       
    </slot>
</div>

<style scoped>
h1{
    color: red;
}
</style>
    <!-- promise was fulfilled -->