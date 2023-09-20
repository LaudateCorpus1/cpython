if (!String.prototype.includes) {
    String.prototype.includes = function (search, start) {
        if (typeof start !== 'number') {
            start = 0;
        }
        if (start + search.length > this.length) {
            return false;
        } else {
            return this.indexOf(search, start) !== -1;
        }
    };
}
if (!String.prototype.endsWith) {
    String.prototype.endsWith = function (searchString, position) {
        var subjectString = this.toString();
        if (typeof position !== 'number' || !isFinite(position) || Math.floor(position) !== position || position > subjectString.length) {
            position = subjectString.length;
        }
        position -= searchString.length;
        var lastIndex = subjectString.indexOf(searchString, position);
        return lastIndex !== -1 && lastIndex === position;
    };
}
if (!String.prototype.startsWith) {
    String.prototype.startsWith = function (search, pos) {
        return this.substr(!pos || pos < 0 ? 0 : +pos, search.length) === search;
    };
}

function toggleNavbar() {
    var nav = document.getElementById("sidenav");
    var navDark = document.getElementById("nav-dark");
    var body = document.getElementsByTagName("body")[0];

    if (window.navbarVisible == true) {
        window.navbarVisible = false;
        nav.classList.add("invisible");
        navDark.classList.add("invisible");
        body.style.cssText = "--sidenav-display: none;";
    } else {
        window.navbarVisible = true;
        nav.classList.remove("invisible")
        navDark.classList.remove("invisible");
        body.style.cssText = "--sidenav-display: block;";
    }
}

function toggleLangpicker() {
    var langpickerWrap = document.getElementById("langpicker-wrapper");
    if (langpickerWrap.style.display == "none") {
        langpickerWrap.style.display = "block"
    } else {
        langpickerWrap.style.display = "none"
    }
}

function navigateLang(lang) {
    var oldLocation = location.href.split("/unicode").reverse()[0];
    location = "/" + lang + "/unicode" + oldLocation;
}

document.getElementById("langpicker").onclick = function () {
    event.stopPropagation();
}


function toggleMobileSearch(focus) {
    var logo = document.getElementById("head-logo")
    var langpicker = document.getElementById("head-langpicker")
    var search = document.getElementById("head-search")
    var header = document.getElementById("header")
    var searchButtonIcon = document.getElementById("head-search-button-icon")

    if (window.mobileSearchVisible == true) {
        window.mobileSearchVisible = false
        langpicker.classList.remove("mobile-search-visible");
        logo.classList.remove("mobile-search-visible");
        search.classList.remove("mobile-search-visible");
        searchButtonIcon.classList.remove("mobile-search-visible");
        header.classList.remove("mobile-search-visible");

    } else {
        window.mobileSearchVisible = true
        langpicker.classList.add("mobile-search-visible");
        logo.classList.add("mobile-search-visible");
        search.classList.add("mobile-search-visible");
        searchButtonIcon.classList.add("mobile-search-visible");
        header.classList.add("mobile-search-visible");
        if (focus != false)
            search.getElementsByTagName("input")[0].focus();
    }
}

function highlightNavigationItem() {
    var currentItem;
    if (location.href.includes("search")) {
        return;
    } else if (location.href.includes("charsets")) {
        currentItem = document.getElementById("navi-charsets");
    } else if (location.href.includes("plane")) {
        currentItem = document.getElementById("navi-plane");
    } else if (location.href.includes("block")) {
        currentItem = document.getElementById("navi-block");
    } else if (location.href.includes("category")) {
        currentItem = document.getElementById("navi-category");
    } else if (location.href.includes("bidiclass")) {
        currentItem = document.getElementById("navi-bidiclass");
    } else if (location.href.includes("combining")) {
        currentItem = document.getElementById("navi-combining");
    } else if (location.href.includes("decomposition")) {
        currentItem = document.getElementById("navi-decomposition");
    } else if (location.href.includes("mirrored")) {
        currentItem = document.getElementById("navi-mirrored");
    } else if (location.href.includes("scripts")) {
        currentItem = document.getElementById("navi-scripts");
    } else if (location.href.includes("html")) {
        currentItem = document.getElementById("navi-html");
    } else if (location.href.includes("references")) {
        currentItem = document.getElementById("navi-references");
    } else if (location.href.endsWith("/unicode") || location.href.endsWith("/unicode/")) {
        currentItem = document.getElementById("navi-main");
    }


    if (currentItem != undefined) currentItem.classList.add("current-item");
}

document.addEventListener("DOMContentLoaded", function () {
    highlightNavigationItem();
    if (window.location.search != "") {
        window.mobileSearchVisible = false;
        toggleMobileSearch(false);
    }
})

if (document.readyState === "complete" || document.readyState === "loaded" || document.readyState === "interactive") {
    highlightNavigationItem();
    if (window.location.search != "") {
        window.mobileSearchVisible = false;
        toggleMobileSearch(false);
    }
}

if (window.matchMedia('(display-mode: standalone)').matches) {
    var logoHref = document.getElementById("head-logo-href")
    logoHref.setAttribute("href", location.origin + location.pathname.match(/\/\w+\/unicode/) + "/")
}

function displayGrid() {
    var gridFrames = document.getElementsByClassName("list-grid-frame")
    for (let i = 0; i < gridFrames.length; i++) {
        gridFrames[i].classList.remove("display-table")
    }
    var tableButtons = document.getElementsByClassName("button-display-table");
    var gridButtons = document.getElementsByClassName("button-display-grid");
    for (let i = 0; i < tableButtons.length; i++) {
        tableButtons[i].classList.remove("active")
    }
    for (let i = 0; i < gridButtons.length; i++) {
        gridButtons[i].classList.add("active")
    }
}

function displayTable() {
    var gridFrames = document.getElementsByClassName("list-grid-frame")
    for (let i = 0; i < gridFrames.length; i++) {
        gridFrames[i].classList.add("display-table")
    }
    
    var tableButtons = document.getElementsByClassName("button-display-table");
    var gridButtons = document.getElementsByClassName("button-display-grid");
    for (let i = 0; i < tableButtons.length; i++) {
        tableButtons[i].classList.add("active")
    }
    for (let i = 0; i < gridButtons.length; i++) {
        gridButtons[i].classList.remove("active")
    }
}

var deferredPrompt;

window.addEventListener('beforeinstallprompt', function (e) {
    // Prevent Chrome 67 and earlier from automatically showing the prompt
    e.preventDefault();
    // Stash the event so it can be triggered later.
    deferredPrompt = e;
    document.getElementById("app-install").style.display = "block";
});

function installApp() {
    deferredPrompt.prompt();
}

window.addEventListener('appinstalled', function (evt) {
    document.getElementById("app-install").style.display = "none";
});

function charNext() {
}

function charPrev() {
}

function blockNext() {
}

function blockPrev() {
}