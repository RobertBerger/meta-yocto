1) create a new repo on github

meta-openembedded-core

2) add my-scripts dir

cd meta-openembedded-core

echo "# meta-openembedded-core fork" >> README.md

git init

git add .

git commit -m "first commit"

git remote add origin git@github.com:RobertBerger/meta-phytec.git

git push -u origin master

3) use my repo

mv meta-openembedded-core meta-openembedded-core.ori
git clone git@github.com:RobertBerger/meta-openembedded-core.git

4) add upstream

cd meta-openembedded-core

git remote add official-upstream https://github.com/openembedded/openembedded-core.git

$ git fetch official-upstream

git branch -a
* master
  remotes/official-upstream/2011-1
  remotes/official-upstream/daisy
  remotes/official-upstream/danny
  remotes/official-upstream/denzil
  remotes/official-upstream/dizzy
  remotes/official-upstream/dora
  remotes/official-upstream/dunfell
  remotes/official-upstream/dylan
  remotes/official-upstream/fido
  remotes/official-upstream/gatesgarth
  remotes/official-upstream/hardknott
  remotes/official-upstream/honister
  remotes/official-upstream/jethro
  remotes/official-upstream/kirkstone
  remotes/official-upstream/krogoth
  remotes/official-upstream/langdale
  remotes/official-upstream/master
  remotes/official-upstream/master-next
  remotes/official-upstream/mickledore
  remotes/official-upstream/morty
  remotes/official-upstream/nanbield
  remotes/official-upstream/pyro
  remotes/official-upstream/rocko
  remotes/official-upstream/rocko-next
  remotes/official-upstream/scarthgap
  remotes/official-upstream/styhead
  remotes/official-upstream/sumo
  remotes/official-upstream/thud
  remotes/official-upstream/walnascar
  remotes/official-upstream/walnascar-next
  remotes/official-upstream/warrior
  remotes/official-upstream/whinlatter
  remotes/official-upstream/wrynose
  remotes/official-upstream/zeus
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
...

$ git tag -l
2011-1
2018-10.4-thud
2019-04.2-warrior
2019-04.3-warrior
2019-04.4-warrior
2019-10.1-zeus
2019-10.2-zeus
2019-10.3-zeus
2019-10.4-zeus
2020-04.1-dunfell
2020-04.2-dunfell
2020-04.3-dunfell
2020-04.4-dunfell
2020-04.5-dunfell
2020-04.6-dunfell
2020-10.2
2020-10.2-gatesgarth
2020-10.3
2020-10.3-gatesgarth
uninative-1.0
uninative-1.3
uninative-1.4
uninative-1.5
uninative-1.6
uninative-1.7
uninative-1.8
uninative-1.9
uninative-2.0
uninative-2.1
uninative-2.10

...

5) use the master branch on a specific commit and make own branch

git co official-upstream/master

git co 2bb062e403c7093734de6467c49503a7d8970d9e

git branch 2026-08-11-training

#5) use specific upstream branch/commit and make own branch
#
#syntax: git fetch url-to-repo branchname:refs/remotes/origin/branchname
#
#$ git fetch git://github.com/STMicroelectronics/meta-st-stm32mp dunfell:refs/remotes/origin/dunfell
#
#From git://github.com/Freescale/meta-freescale
# * [new branch]        dunfell    -> origin/dunfell
#

#6) Update from upstream:
#git co master
#>> git remote -v
#
#official-upstream       git://github.com/Freescale/meta-freescale (fetch)
#official-upstream       git://github.com/Freescale/meta-freescale (push)
#origin  git@github.com:RobertBerger/meta-freescale.git (fetch)
#origin  git@github.com:RobertBerger/meta-freescale.git (push)
#
#>> git fetch official-upstream
#remote: Counting objects: 4043, done.
#remote: Compressing objects: 100% (1273/1273), done.
#remote: Total 4043 (delta 3130), reused 3632 (delta 2727)
#Receiving objects: 100% (4043/4043), 721.50 KiB | 402.00 KiB/s, done.
#Resolving deltas: 100% (3130/3130), completed with 502 local objects.
#From git://git://github.com/Freescale/meta-freescale
#   62591d9..e758547  master     -> official-upstream/master
# + 2942327...a382678 master-next -> official-upstream/master-next  (forced update)
#   a3fa5ce..6a1f33c  morty      -> official-upstream/morty
#---
#

6) hack the branch and update

6.1) hack it

6.2) add/commit

6.3) What was changed?

$ git diff 2021-06-09-3ba7567532bcda55d9d73deff80a350877b68d07-pd21.1.0-stm-dunfell --stat
 conf/layer.conf                                                           | 2 +-
 recipes-bsp/u-boot/{u-boot_2020.01.bbappend => u-boot_2020.01.bbbbappend} | 0
 2 files changed, 1 insertion(+), 1 deletion(-)

7) push upstream:
git co master
cd my-scripts
./push-all-to-github.sh

#8) apply patches
#
#cd meta-virtualization
#
#git co 2019-09-09-warrior-2.7+
#
#stg init
#
#stg series
#
#stg import --mail ../meta-virtualization-patches/2019-09-09-warrior-2.7+/0001-use-systemd-as-cgroup-manager-for-docker-While-it-s-.patch
#
#import all patches
#
#...
#
#stg series
#
#stg commit --all
#
#git log
#
#git co master
#
9) push to my upstream

my-scripts/push-all-to-github.sh

