# Summary week 2
A convolution layer is a layer which applies filter over the image. These filters are used to find features in the images. Like Depth, edges, colours, objects, segmentations etc.

Exercises MLflow

Conclusions from the testing:

    Granularity of the network and epochs give the most performance.
    

    It took some time to fiddle around with kernelsizes to understand what really was happening.
    I think each layer is like a stacked if funtion. That makes it more logical in the case of images to start of with an equal number of inputs to the images. Then slowly trading granularity of the image in for granularity of the filters. The filters combinations are of size 28*28*512*265 en soforth. This gives a lot of different combination possibilitys.

    Performance differences were not that large. Making sure the inputs were mathing gives the largest jump in performance.
    Kernelsizes steer granularity en padding is more or less like a cropping function.

    Hourglass shaped seems logical. And gives the best performance.

    Normalizing layer and dropout did not seem to have much effect. At some point I need to investigate further.

    test

    The unchanged models performance is about 0.0983

    Change1: filters to 8 to make sure when the linearlayers are reached that there are more input nodes then output nodes.

    This raised the performance to 0.1005 but jumped lower after the 2nd epoch

    Change2: the epocs to 4 to see if it jumping over the minimum

    This was the case in the pre last epoch the performance was worse then the 2nd and last

    Change3:
    filters to 64 and layers to 5. this made the flatten size to 64, 128
    I expect to raise the accuracy by this. More hidden patterns should be found.
    Performance was 0.5372
    I the last epoch it jumped 20%

    Change4: maxpool size to 2 and matching units first linear layer

    I expect the result to perform better, because the network is larger. However the jump from 1st to 2nd is big so maybe we need another step there.

    The performance went up to 0,66

    Change:5
    The jump from lineaer layer 1 and to was huge. so i added 2 steps.
    I expect the learnign to be more smooth so the performance jumps more equal. Next to that a better performance.

    Result: performance 0.6442, learning was also not smoother.

    Change: filter to 1024, matching units, kernel and maxpool to 3. So more patterns over larger area

    result:
    Training would have costed extreme long time. Abort

    Change: filters to 128 maxpool to 2 and kernel to 3. mathing units in linear layer.

    expect. Normal training time and good performance.

    Result 0.6706 and ok training.

    Conlusion after these tests is that granularity achieved by the maxpooling and enough filters give a better performance.
    More epochs are needed to se what the maximum becomes. The last performance jump was still 10%

    Change epoch from 4 to 8.
    Expect: better result. close to 85%

    Result: 0.7386 8 min

    Change: add dropout layer change back to 4 epochs.
    Result should be better, than 0.6706

    Resutl was 0.6587
    So slightly less performant than without this

    Change: dropout after every layer of 0.2 as gemini suggested

    Better result then last model
    Result: 0.6778
    So slightly better then last model.

    I'm not sure what to expect from the normalizing layer

    I added after each linear 1

    I found out that some test are not valid. This is because the model is set in 2 places.

    New model build up created.
    Change filters 512, 256, 64, units 128,64,32
    performance 0.4503

    Change filters visa versa.

    Expected result is worse.
    performance = 0.4306

    Change the filters to be 3 * 256
    Expected performance is equal
    Performance was actually a bit better 0.4820

    Changed the units to 256 128, 64
    I expect the performance to be a little bit better. Maybe the learning also smoother
    performance 0.4545

    Changed something

    performance 0.5841



