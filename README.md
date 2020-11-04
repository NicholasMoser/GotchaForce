# Gotcha Force

Investigating some things about the GameCube title Gotcha Force.

## VS Mode Okizeme

When you knock a CPU down in Versus Mode, they get a second of invincibility on wakeup. However in Challenge and Story Mode when you knock a CPU down, they have no invincibility on wakeup. This means when you knock them down in Challenge and Story Mode you can get [okizeme](https://www.dustloop.com/wiki/index.php?title=Okizeme) on them, making the game arguably much more interesting.

It would be nice to have that okizeme for VS Mode. The game would reset to neutral every punish.

## Wake Up Invincibility

The invincibility counter gets set to the float 60.0 at instruction 0x8005d4b0. This is set using a static constant in memory at 0x80437448.

Here is the call stack at this point:
![Call Stack](/call_stack.PNG?raw=true "Call Stack")

It also apparently gets set at the instruction 0x8005c7d8.

It counts down at the instruction 0x80055c00.

## Disable Wake Up Invincibility

```gecko
04437448 00000000
```

The Gecko Code is as simple as setting the static constant in memory from 60.0 to 0.

[Example](https://imgur.com/a/xREgRq1)
