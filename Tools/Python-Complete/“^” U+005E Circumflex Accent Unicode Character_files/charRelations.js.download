function setupCharRelations() {
    for (let j = 0; j < document.getElementsByClassName("list-grid-frame").length; j++) {
        const frame = document.getElementsByClassName("list-grid-frame")[j];
        const contentItems = frame.getElementsByClassName("content-item");
        if ( ((contentItems.length * 146) - 6) > frame.offsetWidth) {
            const button = frame.getElementsByClassName("more-button")[0]
            button.style.display = ""
            for (let i = 0; i < Math.floor((frame.offsetWidth + 6) / 146); i++) {
                contentItems[i].style.display = "";                
            }
            button.addEventListener("click", function(a) {
                button.style.display = "none"
                for (let k = 0; k < contentItems.length; k++) {
                    contentItems[k].style.display = "";
                    
                }
            })
        } else {
            for (let k = 0; k < contentItems.length; k++) {
                contentItems[k].style.display = "";
            }
        }
    }
}

document.addEventListener("DOMContentLoaded", function() {
    setupCharRelations();
})

if (document.readyState === "complete" || document.readyState === "loaded" || document.readyState === "interactive" ) {
    setupCharRelations();
}