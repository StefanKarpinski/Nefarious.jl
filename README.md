# Nefarious

Package demonstrating why `julia --project` in a directory you don't trust can be dangerous, which is why Julia doesn't do `julia --project` automatically, instead requiring you to explicitly add the flag, which constitutes a conscious indication that you trust the project you are in.

Try it out (if you dare!):

```sh
$ cd Nefarious
$ julia -q --project
julia> using JSON
Haha, gotcha!
```

The same attack could easily be expanded to all common package names by just replicating what has been done here for JSON.
If you start a `julia` process in this directory with `--project` you cannot safely load any packages.
If you have a `~/.julia/config/startup.jl` file and it loads any packages, then just starting `julia --project` in this directory could execute arbitrary code.
