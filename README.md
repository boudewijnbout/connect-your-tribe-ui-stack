# Visitekaartje V2 UI Stack

## Wireflow & Breakdown

<img width="500" src="https://github.com/boudewijnbout/connect-your-tribe-fdnd-visitekaartje/blob/main/assets/images/20220224_151040.jpg">

## Code

HTML:

```html
<div class="preloader-wrapper">
  <span class="preloader"></span>
</div>
```

JavaScript:
```javascript
const memberId = 18;
const apiUrl = "https://tribe.api.fdnd.nl/v1/member";

// Personal Card
const nameTitle = document.querySelector("#name-title");
const bio = document.querySelector("article");
const bioText = document.querySelector("article p");
const waveIcon = document.querySelector("article p span");

// Preloader
const preLoaderWrapper = document.querySelector(".preloader-wrapper");

// Fetch API data
fetch(apiUrl)
  .then((res) => {

    if (res.status >= 200 && res.status <= 299) {
      // preLoaderWrapper.classList.add("hide");
      return res.json();
    } else {
      preLoaderWrapper.classList.add("hide");
    }
  })

  // Filter data to specific person
  .then((res) => {
    const boudewijnData = res.data.find((student) => student.memberId === 18);

    // Put data into HTML

    // Title
    nameTitle.textContent = `${boudewijnData.name} ${boudewijnData.surname}`;

    // Bio
    bioText.textContent = boudewijnData.bio;
  })
