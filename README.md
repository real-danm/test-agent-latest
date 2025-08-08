make sure you have a project selected with lk project set-default

make sure you have a .env with secrets

run lk agent create

you can paste this in your zshrc/bashrc/etc and then run `lkmp` to create new custom meet windows that should connect to this deployed agent
```
lkmp() {
    local active_url=$(lk project list | grep '\*' | awk '{print $5}')
    # local token=$(lk token create --identity abc --room test --join | grep 'Access token:' | awk '{print $3}')
    local token=$(lk token create --identity abc --room abcdefg$(date +%d%H%M%S) --join | grep 'Access token:' | awk '{print $3}')
    local url="https://meet.livekit.io/custom?liveKitUrl=${active_url}&token=${token}"
    open -a "Google Chrome" "$url"
}
```
