Summary of the tests.

Again the network improves the most from adding depth in layers or width to improve accuracy.
Adding to much depth to the model however frequently resulted in early stopping of the training. I had not seen this in the post assignments and some of it could be resolved by adding more depth.

model:
It seems logical to me that the length of the hidden_size is equal to the lenght of the hidden_size of the linear model.
I did not understand the transformation of the tensor.
From the notebooks I understood that the tensor was Batch*Features*timesteps. Maybe the model does this by creating the hidden_state. It is however then unclear how big the hiddenstate should be. Is it F*F*F? or F*T? It is not the first the model cant handle this. So how does it work?

ALso the padding system is not clear to me. I'm expecting to only havve to add 0 on the end of the second dimension of the tensor. Not sure how this works in the notebook. Also when working in batches how could you do this just in time and end up with equal lengths?

epochs:
Again the epochs have a great influence on the performance of the model. What surprises me though that the steps are always very tiny. Also on the start of the training. I'm expecting the gradients to be steep here so also seeing big jump in performance increase.


TESTS:


First setup config = ModelConfig(
        input_size=3,
        hidden_size=52,
        num_layers=1,
        output_size=20,
        dropout=0.2,
    )
Expectation was a fairly goof score. It stopped because of early stopping at 0.0422

Change the numbe of layers to 5
Expectation is that the score will be better but the learning slower.

score: 0.2297 learning time was longer

Change back to 1 layer but more hidden_size features*timesteps = 150
I expect a similar score but because the netowrk got wider instead of deeper.

score 0.1750

Change hidden_size to double 300

I expect a small improvement, i expect the network already to be to wide. 0.3187

This was different then i thought and had actually more improvement.

Change depth to 3 and hidden_size to 150
THis had more parameters then either one choice.

I expect to go to 50+

performance:
0.2766 early stop. only 5% more then 5 layers and size 52

Now deep and wide:
150 + 5 layers
should perform better then 0.3187

performance at 0.4156

Change layers to 10
I expect it to stop early.
It did not stop early. performance was weak like 30%

back to 51 hidden_size

0.1359 early stop.

Change to 300 and 10 performance = 0.4078





