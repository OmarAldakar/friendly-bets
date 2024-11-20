<script lang="ts">
    let betChoices = $state([{choice: ""}]);

    function addChoice() {
        betChoices.push({choice: ""});
    }

    function onChoiceChange(i: number) {
        if (betChoices.length > 1 && betChoices[i].choice == "") {
            betChoices.splice(i, 1)
            return
        }
        if (i == betChoices.length - 1 && betChoices[i].choice != "") {
            addChoice();
        }
    }
</script>

<div class="flex justify-center items-center min-h-screen bg-gray-50 px-4 sm:px-6">

<form class="bg-white m-6 p-6 rounded-lg shadow-md space-y-6 w-full max-w-lg">
    <h2 class="text-2xl font-bold text-gray-700">Create a Bet</h2>

    <!-- Title -->
    <div>
        <label for="title" class="block text-sm font-medium text-gray-700">Bet Title</label>
        <input type="text" id="title" name="title" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Enter the bet title" required>
    </div>

    <!-- Options -->

    <div>
        <label for='option1' class="block text-sm font-medium text-gray-700">Options</label>
        {#each betChoices as elt, i}
            <div class="space-y-2 mt-2">
                <input oninput={(_) => onChoiceChange(i)} bind:value={elt.choice} type="text" name="option{i}" class="block w-full rounded-md border-gray-300 shadow-sm focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Option {i + 1}">
            </div>
        {/each}
    </div>

    
    <!-- Start Date -->
    <div>
        <label for="start_date" class="block text-sm font-medium text-gray-700">Bet is starting at</label>
        <input type="datetime-local" id="start_date" name="start_date" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:ring-blue-500 focus:border-blue-500 sm:text-sm" required>
    </div>

    <!-- Submit Button -->
    <button type="submit" class="w-full bg-blue-600 text-white py-2 px-4 rounded-md hover:bg-blue-700 focus:ring-2 focus:ring-blue-500 focus:ring-offset-2">
        Create Bet
    </button>
</form>
</div>