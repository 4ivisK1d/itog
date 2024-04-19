<script>
    let newTitle = "";
    let newDesc = "";
    let movieList = [];
    function add() {
        if (newTitle !== "" && newDesc !== "") {
            movieList = [
                ...movieList,
                {
                    title: newTitle,
                    description: newDesc,
                },
            ];
            newTitle = "";
            newDesc = "";
        }
    }
</script>

<svelte:head>
    <title>Кинотеатр</title>
</svelte:head>

<div class="container">
    <h1>Кинотеатр</h1>
    <form on:submit|preventDefault={add} >
        <input bind:value={newTitle} placeholder="Название" />
        <input bind:value={newDesc} placeholder="Описание" />
        <button class="add-todo" on:click={add}><span>+</span></button>
    </form>

    <div class="apps">
        {#each movieList as movie}
        <div class="movie" id="movie">
            <div class="movie-info" id="MovieInfoDiv">
                <h3 id="MovieTitle">{movie.title}</h3>
                
            </div>
            <div class="overview">
                <h3 id="Description">{movie.description}</h3>
            </div>
        </div>
        {/each}
    </div>
</div>
<style>
     :root {
    --primary-color: rgb(155, 213, 252);
    --secodary-color: rgb(103, 170, 247);
}
   .container {
    display: flex;
    flex-direction: column;
    align-items: center;
   }
    h1 {
        text-align: center;
    }
    form {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        max-width: 400px;
        width: 100%;
        padding: 20px;
    }
    input {
        width: 100%;
        padding: 10px;
        margin: 10px 0;
        box-sizing: border-box;
    }
    button {
        width: 100%;
        padding: 10px;
        margin: 10px 0;
    }
    button:hover {
        background-color: #ddd;
    }
    button:active {
        background-color: #bbb;
    }
    button:focus {
        outline: none;
    }
    button:disabled {
        background-color: #ccc;
    }
   .apps {
    /* width: 400px;
    margin: 0 auto;
    */
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
   }
  
   .movie {
    width: 300px;
    margin: 10px;
    background-color: var(--secodary-color);
    box-shadow: 0 4px 5px rgba(0, 0, 0, 0.2);
    position: relative;
    overflow: hidden;
    border-radius: 3px;
}



.movie-info {
    color: black;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 30px 30px;
    letter-spacing: 0.5px;
}

.movie-info h3{
    margin-top: 0;
}



.overview {
    background-color: white;
    padding: 20px;
    position: absolute;
    left: 0;
    bottom: 0;
    right: 0;
    max-width: 100%;
    transform: translateY(101%);
    transition: transform 0.3s ease-in;
}

.movie:hover .overview{
    transform: translateY(0)
}


</style>

