(() => {
   
    const mobileWidth = 780; //for smaller screens
    
    //main navigation, the background will be added as soon as it is scrolled.
    const addMenuBackground = () => {
        const pageWidth = window.innerWidth;
        const bodyOffSet = document.body.scrollTop || document.documentElement.scrollTop;
        const navigation = document.querySelector('header nav');
        
        if(pageWidth > mobileWidth) {
            bodyOffSet > 0 ? navigation.classList.add("tfp-nav-fixed") : navigation.classList.remove("tfp-nav-fixed");
        }   
    }
    
    //for the mobile screens, the mav bar is changed into the menu
    //what happens in this function that wheneer the size of the webpage is reduced the nav bar elemnts are taken to the body and when webpage is enlarged again then nav menu bar is shifted again to its place in header
    
    const reorderResponsive = () => {
        const pageWidth = window.innerWidth;
        const navContainer = document.querySelector("header nav .tfp-container");
        const navigation = document.querySelector("header nav .tfp-navigation");
        const mobileNavigation = document.querySelector("body > .tfp-navigation");
        
        if(pageWidth <= mobileWidth && navigation){
        document.body.insertAdjacentElement("afterbegin",navigation);
        } else if (pageWidth > mobileWidth && mobileNavigation) {
            navContainer.insertAdjacentElement("beforeend", mobileNavigation);
        }
    }
    
    // to scroll smoothly to the particular section when clicked on the navigation bar
    
    const onNavItemClick = () => {
        const navItemList = document.querySelectorAll(".tfp-section-link");
        const navItems = [...navItemList];
        
        navItems.forEach(item => {
            item.addEventListener("click", event => {
                event.preventDefault();
                
                const sectionId = event.target.getAttribute("href") || event.target.dataset.href;
                
                
                //function will scroll to the certain part of the application
                scrollToSection(sectionId);
            })
        })
    }
    
    const scrollToSection = sectionId => {
        let sectionPosition, sectionOffSet;
        const navigationHeight = document.querySelector("header nav").offsetHeight;
        const pageWidth = window.innerWidth; 
        
        if(sectionId !== "#"){
            sectionOffSet = document.querySelector(sectionId).offsetTop;
            sectionPosition = pageWidth > mobileWidth ? sectionOffSet - navigationHeight : sectionOffSet; //this is done so that the nav bar won't cover the section of the page.
           
           }
        else {
           sectionPosition = 0; // it will lead us to the top of the page
           }   
        
        window.scrollTo({
            'behavior' : 'smooth',
            'left' : 0,
            'top' : sectionPosition
        })
        
    }
    
    //function so that the blogs can be changed through the arrow functions
    
    const onBlogChange = () => {
        let firstChild, lastChild;
        const prevArrow = document.querySelector("#tfp-blog-prev");
        const nextArrow = document.querySelector("#tfp-blog-next");
        const blog = document.querySelector(".tfp-blog ul");
        
        document.addEventListener("click", () => {
            if(event.target === prevArrow){
               lastChild = blog.lastElementChild;
                blog.insertAdjacentElement("afterbegin" , lastChild);
               } else if (event.target === nextArrow) {
                   //this will lead the first blog to the end of the unordered list, so the next blog will be visible.
                firstChild = blog.firstElementChild;
                blog.insertAdjacentElement("beforeend" , firstChild);
            }
        })
    }
   
    /*
    
    //to maximize the size of the gallery image when clicked at te end of the page
    const onGalleryImageClick = () => {
        const galleryImageList = document.querySelectorAll("#tfp-gallery li");
        const galleryImages = [...galleryImageList];
        
        galleryImages.forEach(image => {
            image.addEventListener("click", event => {
                galleryImageOpen(event.target); //the function by creating image will be opened
            })
        })
    }
    
    const galleryImageOpen = image => {
        const imageSrc = image.getAttribute("src");
        const openedImage = `<div class = 'tfp-backdrop'><img src ='${imageSrc}' alt = ''/>
                             <span class = 'tfp-backdrop-close'>X</span></div>`;
        
        document.body.insertAdjacentHTML("beforeend", openedImage);
        
        galleryImageClose();
    }
      
    const galleryImageClose = () => {
        const closeButton = document.querySelector(".tfp-backdrop-close");
        
        closeButton.addEventListener("click", () => {
            const backdrop = document.querySelector(".aw-backdrop");
            backdrop.remove();
        })
    }
    */
    window.addEventListener("scroll" , () => {
        addMenuBackground();
    })
      
    window.addEventListener("resize" , () => {
      reorderResponsive();
    })
    
    onNavItemClick();
    onBlogChange();
    /*onGalleryImageClick(); */
    reorderResponsive();
    
})()
