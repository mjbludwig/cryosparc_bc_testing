# Cryosparc OOD app

This is a slap-dash README, email m_ludwig@techsquare.com or and maybe just as good, leave a git issue if you have questions or comments. 


### Pre-reqs

This app assumes a bit of somewhat standard OOD setup along with some cryosparc install work that goes beyond the barebones install of OOD. What I can remember off the top of my head is the following.

* OOD configured for Interactive Desktops, specifically the vnc bits: https://osc.github.io/ood-documentation/latest/app-development/interactive/setup.html
* compute nodes have xfce installed, most easily done with `yum group install ...`
* Cryosparc is already installed in a user specific dir, with a port already chosen at install based on some UID -> unique port math, see `template/script.sh.erb` for the logic. 
* Cryosparc install also needs a password defined at install (maybe adjustable in the config after the fact) so this app assumes the user knows that password.
* Some sort of Firefox install, in this case as an Environment Module

### Important things to remember

* Remember to set the "cluster" config in `form.yml.erb` for your cluster
* Cryosparc takes a few seconds to start up fully so if atm you may run into firefox opening automatically and trying to hit the local port before Cryosparc has fully started, requireing a page refresh. 
* Cryosparc is _very_ particular with lock files, most importantly `/tmp/cryosparc*sock`. See the cleanup section of `template/script` to get a sense. 
* Most of the cleanup is functional and needed but the `trap 'cleanup' SIGINT SIGQUIT SIGTERM SIGKILL` is not really working at this point as the "script.sh.erb" script is actually called as a child process of the actual OOD sbatch script under the hood so it does not actually receive the SIG calls from an scancel that are necessary to clean up properly. 



**ADD MORE HERE**
