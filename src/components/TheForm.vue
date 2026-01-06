<template>
    <form>
        <div class="form-control">
            <div>
                <label for="first-name">First Name <span>*</span></label>
                <input type="text" id="first-name" name="first-name">
            </div>
            <div>
                <label for="last-name">Last Name <span>*</span></label>
                <input type="text" id="last-name" name="last-name">
            </div>
        </div>
        <div class="form-control">
            <label for="age">Age <span>*</span></label>
            <input type="number" id="age" name="age">
        </div>
        <div class="form-control">
            <h2>Are you attending? <span>*</span></h2>
            <div>
                <input type="radio" name="attending" id="yes">
                <label for="yes">Yes</label>
            </div>
            <div>
                <input type="radio" name="attending" id="no">
                <label for="no">No</label>
            </div>
        </div>
        <div class="form-control">
            <h2>Your meal Selection</h2>
            <div>
                <input type="checkbox" name="meal" id="meal-chicken">
                <label for="meal-chicken">Chicken</label>
            </div>
            <div>
                <input type="checkbox" name="meal" id="meal-fish">
                <label for="meal-fish">Fish</label>
            </div>
            <div>
                <input type="checkbox" name="meal" id="meal-salad">
                <label for="meal-salad">Salad</label>
            </div>
        </div>
        <div class="form-control">
            <label for="guest">Are you bringing a guest? <span>*</span></label>
            <select name="guest" id="guest">
                <option value="yes">Yes</option>
                <option value="no">No</option>
            </select>
        </div>
        <div class="form-control">
            <input type="checkbox" name="confirm-terms" id="confirm-terms">
            <label for="confirm-terms">Agree to the terms of guest?</label>
        </div>
        <div>
            <button>Add Guest</button>
        </div>
    </form>
</template>