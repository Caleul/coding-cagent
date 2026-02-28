To run this you need to:

install docker
brew install cagent

Download your model or point an API key (not sure how to use API keys on Cagent) and run with:

cagent run coding-agent.yaml

For better experience while using I saved the file in the folder `~/.cagent/` and create a alias to run it 

```
alias ccode="cagent run ~/.cagent/coding-agent.yaml"
```

By doing this i can run it in the terminal of any repository just with the comando `ccode`
