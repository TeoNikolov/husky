<script lang="ts">
    function getRandomHuskyImage() {
        fetch('https://dog.ceo/api/breed/husky/images/random')
            .then(response => response.json())
            .then(data => {
                const imageElement = document.getElementById('image-frame') as HTMLImageElement;
                imageElement.src = data.message;
            })
            .catch(error => {
                const errorElement = document.getElementById('error-message') as HTMLDivElement;
                errorElement.textContent = 'Failed to load image: ' + error.message;
                console.error('Error fetching image:', error);
            });
    }
</script>


<div class="flex flex-col items-center justify-center min-h-screen bg-gray-400 px-4 py-10">
    <div class="w-full max-w-[40em] flex flex-col items-center justify-center bg-gray-100 rounded-3xl p-6">
        <div class="text-left">
            <h1 class="text-3xl text-gray-800 mb-12"><span class="font-bold">Welcome!</span>
                <br>
                This is a page about all-things-husky.
            </h1>
            <h2 class="text-2xl text-gray-700">Currently you can only get random husky pics.</h2>
        </div>

        <div id="image-container" class="mt-6 w-full max-w-[25em] h-[25em] p-4 flex items-center justify-center border-4 border-gray-500 rounded-4xl shadow-lg bg-white">
            <img id="image-frame" class="w-full h-full object-contain" src="https://raw.githubusercontent.com/TeoNikolov/husky/refs/heads/main/husky.webp" alt="Husky" />
            <div id="error-message" style="color: red;"></div>
        </div>

        <button
            on:click={getRandomHuskyImage}
            class="mt-6 bg-blue-500 hover:bg-blue-600 active:bg-blue-900 text-white font-semibold px-6 py-2 rounded-2xl shadow-lg transition"
            >
            New Husky
        </button>

        <div class="mt-12 space-y-4 max-w-md w-full text-left">
            <p class="text-lg text-gray-600">Images are generated from <a class="font-bold" href="https://dog.ceo/dog-api/">https://dog.ceo/dog-api/</a>.</p>
            <p class="text-lg text-gray-600">Source code: <a class="font-bold" href="https://github.com/teonikolov/husky">https://github.com/teonikolov/husky</a></p>
        </div>
    </div>
</div>
