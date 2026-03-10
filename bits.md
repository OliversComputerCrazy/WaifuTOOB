You can achieve this by **listening to changes on the `AdvancedSelect` dropdown** and showing/hiding elements based on whether “Simple” or “Advanced” is selected. Right now, the NSFW select is always visible. We just need to wrap it in a container and toggle its visibility.

Here’s a step-by-step approach:

---

### 1. Wrap the NSFW select in a container

In your HTML, modify the settings section like this:

```html
<h2>Waifu TOOB Settings</h2>

<div id="simpleSettings">
  <p>Contain NSFW images?</p>
  <select id="NSFWselect">
    <option value="True">Always</option>
    <option value="All">Sometimes</option>
    <option value="False" selected>Never</option>
  </select>
</div>

<div id="advancedSettings" style="display:none;">
  <p>Advanced setting 1: </p>
  <input type="text" placeholder="Enter value" />
  <p>Advanced setting 2: </p>
  <input type="text" placeholder="Enter value" />
</div>
```

Here, `simpleSettings` will show for “Simple” mode, and `advancedSettings` will show for “Advanced” mode.

---

### 2. Add JavaScript to toggle based on the select

Add this snippet **after your DOM content is loaded** (e.g., at the bottom of your `<script>`):

```js
const advancedSelect = document.getElementById('AdvancedSelect');
const simpleSettings = document.getElementById('simpleSettings');
const advancedSettings = document.getElementById('advancedSettings');

function updateSettingsView() {
  if (advancedSelect.value === 'simple') {
    simpleSettings.style.display = 'block';
    advancedSettings.style.display = 'none';
  } else if (advancedSelect.value === 'advanced') {
    simpleSettings.style.display = 'none';
    advancedSettings.style.display = 'block';
  }
}

// Listen for changes
advancedSelect.addEventListener('change', updateSettingsView);

// Initialize on page load
updateSettingsView();
```

---

✅ **What this does:**

* When **Simple** is selected → only the NSFW select shows.
* When **Advanced** is selected → the “Advanced settings” div shows instead.
* Automatically initializes correctly on page load.

---

If you want, I can also **make it so the advanced settings include extra NSFW options or extra controls dynamically**, so it doesn’t just hide/show static inputs — this can make your settings menu fully dynamic.

Do you want me to do that?
