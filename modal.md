## Bootstrap Modal
A *Modal* is a dialog box/popup window that overlay content on a current page. It is made up of three parts, namely **header**, **body** and **footer**. While it is not a requirement to include all three parts when using this component, you are required to at least use one. Otherwise, it defeats the purpose of using it in the first place.

### How it Works?
Firstly, Bootstrap advices us to place our modal at the top most area of our web page so as to not cause any interferences with other surrounded elements. Thus, a good placement is after our closing nav `</nav>`. 
To get started, we will create a div container and provide a few attributes.
```
<div id="modalId" class="modal fade" role="dialog">
.
.
.
</div>
```
Next, we will add another div container inside of the div container we added before. Now, we will give it a class, **.modal-dialog**, which basically sets the proper width and margin of the modal. At this point, your code should look as follows:
```
<div id="modalName" class="modal fade" role="dialog">
    <div class="modal-dialog modal-lg" role="content">
    </div>
</div>
```
At this point, it is time to add a div container that will wrap/contain all of the modal content, thus the class name **.modal-content**. Then inside of that we will add the parts as noted above, **.modal-header**, **.modal-body**, **.modal-footer**, each belonging to its own div.

Our code:
```
<div id="modalName" class="modal fade" role="dialog">
    <div class="modal-dialog modal-lg" role="content">
        <div class="modal-content">

            <!--Modal Header-->
            <div class="modal-header">
                ...
            </div>

            <!--Modal Body-->
            <div class="modal-body">
                .
                .
                .
            </div>

            <!--Modal Footer-->
            <div class="modal-footer">
                ...
            </div>
        </div>
    </div>
</div>
```

For sake of simplicity, we will not be adding much content, only the stuff that are *most* relevant.
On that note, we will now add the close button along with a title to our *modal-header*.
```
...
<div class="modal-header">
    <h4 class="modal-title">
        Modal Title
    </h4>
    <button type="button" class="close" data-dismiss="modal">
        &times; <!--this is an "X" symbol-->
    </button>
</div>
...
```
So far, we would have created our modal but we need to add a trigger element. To do this, we will need to add a few attributes to that element that will be used to trigger our modal.

* **data-toggle="modal"**
* **data-target="#modalId"**

Our code to this point should look as follows:
```
<div id="modalName" class="modal fade" role="dialog">
    <div class="modal-dialog modal-lg" role="content">
        <div class="modal-content">

            <!--Modal Header-->
            <div class="modal-header">
                <h4 class="modal-title">
                    Modal Title
                </h4>
                <button type="button" class="close" data-dismiss="modal">
                    &times; 
                </button>
            </div>

            <!--Modal Body-->
            <div class="modal-body">
                .
                .
                .
            </div>

            <!--Modal Footer-->
            <div class="modal-footer">
                ...
            </div>
        </div>
    </div>
</div>
```

