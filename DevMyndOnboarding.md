## Development Environment Set-up
This is written from the perspective of someone who has spent years working in the Windows world so apologies if it feels like its written for a 5  year old (it kind of is).

1. Install Homebrew: https://brew.sh/
2. Install Xcode
3. Install Xcode command line tools: `xcode-select --install`
4. Install git: `brew install git`

   Possible errors (particularly on High Sierra +):
   * Could not create /usr/local/whatever (may happen for multiple folders)
      
      _Resolution:_ `sudo chown -R $(whoami) /usr/local/*`  
      usr/local can no longer be chown'd in High Sierra (ref: https://github.com/Homebrew/brew/issues/3228#issuecomment-332679274)  
      you can chown everything within it though
      
   * xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
   
      _Resolution:_ `xcode-select --install`  
      git on Mac has a dependency on xcode command line tools, so you need to make sure those are installed (https://stackoverflow.com/questions/32925000/git-doesnt-work-after-upgrading-mac-os-x-el-capitan)
      
   * Error: Permission denied @ dir_s_mkdir - /usr/local/lib
   
      *_Resolution:_ `sudo install -d -o $(whoami) -g admin /usr/local/lib`  
      Then you should be able to run whatever command failed previously
      
   * Error: The `brew link` step did not complete successfully
     The formula built, but is not symlinked into /usr/local
     /usr/local/opt is not writable
     
     _Resolution:_ I _think_ the above resolution will fix this too but tbh I'm not sure what fixed this one since I ran into so many issues and tried so many different things. 
     
5. Install the ruby environment: `brew install rbenv`
6. Install Node Version Manager (nvm): `brew install nvm`

   * If using Homebrew to install doesn't work for you, I found this link to be helpful (https://blog.adriaan.io/macos-sierra-broke-my-git.html or http://nodesource.com/blog/installing-node-js-tutorial-using-nvm-on-mac-os-x-and-ubuntu/)
   * Verify that your .bash_profile file has been modified with a pointer to your nvm directory. Something similar to the following
   
     `export NVM_DIR="$HOME/.nvm"`
    
      `. "/usr/local/opt/nvm/nvm.sh"`
  
   * You may need to restart your terminal or open another window in order to get nvm. You can verify by running `nvm --version`
  
5. Install Ruby (verify which version you should install for your project): `rbenv install your.version.here` (i.e. `rbenv install 2.4.2`)

    * Verify that your .bash_profile file has been modified with a pointer to your Ruby environment.
    
      `export PATH="$HOME/.rbenv/bin:$PATH"`
    
      `eval "$(rbenv init -)"`
       
7. Install Node (verify which version you should install for your project): `nvm install your.version.here` (i.e. `nvm install 6.10.2`)

   * This should automatically set your default Node version to what you just installed, but if you don't see a log msg for `Creating default alias` you can run `nvm alias default your.version.here`

8. Install bundler: `gem install bundler`

9. Install yarn: `brew install yarn` 

   * Don't npm install this, it complains about it: https://yarnpkg.com/en/docs/install

10. Install PostgreSQL: `brew install PostgreSQL`


### Nice to haves
1. [Spectacle](https://www.spectacleapp.com/) - window/pane managment
2. iterm - versions 2 or 3
