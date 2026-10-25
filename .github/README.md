# aquamarine, patched / aquamarine avec correctifs

**English** — Personal build of [aquamarine](https://github.com/hyprwm/aquamarine), Hyprland's
rendering backend: the latest upstream release with a local patch on top, kept aligned
automatically. Built and shipped with
[Hyprland-patched](https://github.com/jpreculeau/Hyprland-patched), which installs the whole stack
on Debian 13 arm64. Not affiliated with the Hyprland project; no pull request is made from this
repository. Use upstream unless you need this patch.

**Français** — Version personnelle d'[aquamarine](https://github.com/hyprwm/aquamarine), le
backend de rendu de Hyprland : dernière version publiée en amont avec un correctif local, alignée
automatiquement. Compilée et distribuée avec Hyprland-patched, qui installe toute la pile sur
Debian 13 arm64. Sans lien avec le projet Hyprland ; aucune pull request n'est faite depuis ce
dépôt. Préférez l'original si ce correctif ne vous sert pas.

## Patch / correctif

**drm: stop retrying the mgpu renderer on the primary GPU when it cannot be created** — on some
setups (Raspberry Pi 5: vc4 display + v3d render node) that renderer cannot be created, and
`initMgpu()` retried it on every commit, logging hundreds of lines per second. The primary GPU only
needs it to blit for secondary GPUs: it is now marked as not required, with one warning, and is
not retried before a restart. / Sur certaines machines (Pi 5) ce renderer ne peut pas être créé et
était réessayé à chaque commit ; il n'est plus requis pour le GPU principal (un seul
avertissement, pas de nouvel essai avant redémarrage).

## Branch / branche

`main`: upstream history is not included. Each upstream release is a single commit `upstream:
vX.Y.Z, unmodified source` (its tree, unchanged), chained to the previous one, with the patch on
top; it moves onto each new release and is force-pushed (`fork/sync.sh` of Hyprland-patched). /
L'historique amont n'est pas inclus : chaque version amont est un seul commit, avec le correctif
par-dessus, déplacé à chaque nouvelle version.

Code assisted by an AI model (Claude); see the `Co-Authored-By` line of the commit. /
Code écrit avec l'aide d'un modèle d'IA (Claude) ; voir la ligne `Co-Authored-By` du commit.
