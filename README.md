# ai visual recognition under 10min

let's create a custom classifier and run analysis with node.red on images.


## steps
1. **create custom classifier** [the drone based image classifier with John Walicki's lab](https://github.com/IBM/drones-iot-visual-recognition)
- see the short video on how the custom classifier was done in Watson Studio for [the wild fires : https://youtu.be/kW7cjuWuPS0](https://youtu.be/kW7cjuWuPS0)

2. **use the visual recognition in Node Red** [use the watson visual recognition service in node.red](https://github.com/watson-developer-cloud/node-red-labs/tree/master/basic_examples/visual_recognition)

3. **add the custom classifier from step one to the above lab in step two** - tweak the lab to use our custom model - the steps are provided below:

add an additional `function` node - see the pic. 

![added-node](images/added-node.png)

![added-function](images/node-function.png)

Wire it together with the visual recogniton node.

add this code:

```js
msg.params={"classifier_ids":["CountBurnedHomes_some_id"],"threshold":0};
return msg;
```

Please mind that you need to replace the classifier_ids' value - ie. `CountBurnedHomes_some_id` with the value from the custom classifier in Watson Studio. You can find it on the asset page. See below picture - in the shown case the classifier_ids' value is `DefaultCustomModel_1017852438` :

![watson-studio-custom-classifier](images/custom-model-watson-studio.png)

And you should be good to test it on image like this one: https://i.dailymail.co.uk/i/newpix/2018/08/10/00/4EF8313400000578-0-image-a-11_1533857657594.jpg (this is such an unhappy picture, that please give a thought to displaced people in Nothern California, and other places affected by disasters. Do [Call for Code!](http://callforcode.org/) ).

```
And one more thing - you can test the new classifier with coreML iOS app - check this recipe: 
```
https://developer.ibm.com/tutorials/watson-visual-recognition-with-core-ml-single-model/

If you like give me a star. Follow me on Twitter: [blumareks](http://twitter.com/blumareks).
BTW. I have a blog. Check it out [my blog on medium](https://medium.com/@blumareks) .
