compass-bootstrap-ex
====================

Compass with modification to work better with bootstrap
---

This modification includes commit https://github.com/trotzig/compass/commit/598c6dd47c04e06ea4211592b296583627b7f473

This commit allow to use backroud position with pecent by typing
    
    <map>-use-percentages : true;
    
Its usefull for creating responsive sprites. That work around on commits didnt worked for me so i created my own modification.

Using  responsive sprites with bootstram is ease, bootstrap has 4 break-points at 1200px 992px 768px 480px;

So, I added background-size property to sprites which solves all problems.
Usage:
    
    @include <sprite-map>-bg-size(<sprite-name>);
    
This will cover background depending on width, so actualy we need to handle height.
Using bootstrap breakpoins - its easy.
Added few more mixin`s to compass to handle media querie properties.

To create responsive sprite with bootstrap fluid grid, use :

    $<map>-use-percentages: true;

    div {
      @include <map>-sprite(<sprite-name>);
      @inclide <map>-sprite-bg-size(<sprite-name>);
      width : <map>-sprite-width(<sprite-name>);
      height : <map>-sprite-height(<sprite-name>);
      
      /** For medium screen   betwen 992 and 1200px lets reduce 25% size **/
      @include md-width(0.75 * <map>-sprite-width(<sprite-name>));
      @include md-heigh(0.75 * <map>-sprite-height(<sprite-name>));
      
      /** Form small screen  between 768 and 992px lets reduce 40% size **/
      @include sm-width(0.6 * <map>-sprite-width(<sprite-name>));
      @include sm-heigh(0.6 * <map>-sprite-height(<sprite-name>));
      
      /** Form extra small screen  between 480 and 768px lets reduce 50% size **/
      @include xs-width(0.5 * <map>-sprite-width(<sprite-name>));
      @include xs-heigh(0.5 * <map>-sprite-height(<sprite-name>));
    }
    
Woking with bootstrap it nessessary to ad only sizes to 4 breakpoints


Mixins added for xs sm md properties like in example.
They create bootstrap media query 
ex. 
        @media(min-width:768px){
        }
        
If you want to use max-width instead of min-width, add seconnd true parametr.
ex.:
        @include sm-font-size(20px,true);
        
will be converted to
        @media (max-width: 992px){
            font-size : 20px;
        }
