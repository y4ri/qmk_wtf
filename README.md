# wtf indeed

- you need to fork qmk_firmware and put your kb files to the `/keyboard/<kb_name>` folder because qmk compile looks up the qmk_firmware repo pointed by `qmk config`

- qmk_userspace is a wrapper that holds ONLY keymaps and those can be in 3 different directories:

```text
keyboards/.../keymaps => they have to be there if you wanna compile
layout => code you reuse (mainly the keycodes assigned, im guessing) accross boards with the same key layout
user => code you reuse across any board you have

keyboards is for specific keyboard, layouts is for boards that support community layouts (like split_3x6_3, aka corne style), and users is for shared code between all boards
```

- `qmk userspace-add -kb dasbob -km default` will add that kb and layout to userspace target file (qmk.json)

- if compilation fails with something-something missing chibios something run:
    - `qmk cd`
    - `qmk git-submodule`
    it will pull dependencies