# train-text-from-scratch

Basic usage instructions:

```bash
# get training data
wget https://github.com/brunoklein99/deep-learning-notes/blob/master/shakespeare.txt

# train
./bin/train-text-from-scratch \
        --vocab-model ../models/ggml-vocab.bin \
        --ctx 64 --embd 256 --head 8 --layer 16 \
        --checkpoint-in  chk-shakespeare-256x16.bin \
        --checkpoint-out chk-shakespeare-256x16.bin \
        --model-out ggml-shakespeare-256x16-f32.bin \
        --train-data "shakespeare.txt" \
        -t 6 -b 16 -n 32 --seed 1 --adam-iter 16 \
        --print-details-interval 0 --predict 16 --use-flash

# predict
./bin/main -m ggml-shakespeare-256x16-f32.bin
```
!./main -t 10 -ngl 32 -m ./models/7B/ggml-vic7b-q4_0.bin --color -c 2048 --temp 0.7 --repeat_penalty 1.1 -n -1 -p "### Instruction: Write a story about llamas\n### Response:"
