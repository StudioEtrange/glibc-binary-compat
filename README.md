# glibc-compat-node-vscode

* Goal

    Build and use a custom glibc runtime to run binaries on older Linux systems where the system glibc is too old.

    Allow to build a custom glibc (script 1) and patch any binary to use the built glibc by linking to it (script 2).
    A typical use case is to be able to use Node.js on legacy systems uch as RHEL/CentOS 7 where the system glibc is tool old for modern Node.js version.

    Another use case is to also allows VS Code Remote SSH to work on older Linux systems by ensuring that the Node.js binary bundled with VS Code Server is patched to use the custom glibc runtime, by deploying a hook at each SSH connexion. (script 3)


* Scripts
  * 1/ `build-custom-glibc-runtime.sh` : build a custom glibc runtime
  * 2/ `patch-with-custom-glibc.sh` : patch a binary so that is uses the custom glibc runtime,
  * 3/ `install-vscode-server-patch-hook.sh` : install a hook in `$HOME/.ssh/rc` to automatically, at each SSH conection, patch the Node.js binary used by VS Code Server under `$HOME/.vscode-server` (NOTE : at the first VS Code Remote SSH connexion, VS Code Server will be downloaded and the included Node.js downloaded version will not be patched, to patch the new downloaded version it requires to reconnect with SSH once again)
  