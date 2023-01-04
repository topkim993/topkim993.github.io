---
layout: single
title: "Iterm 커스텀"
---
{% raw %}  
![Jan-04-2023 13-20-11](https://user-images.githubusercontent.com/57055565/210484195-442efef3-d1b2-4925-843d-7b23f800afa0.gif)


### Oh my zsh 설치
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Auto jump 설치
```
brew install autojump
```

### zsh-autosuggestions 설치
```
brew install zsh-autosuggestions
cd ~/.oh-my-zsh/plugins
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### zsh-syntax-highlighting 설치
```
brew install zsh-syntax-highlighting
cd ~/.oh-my-zsh/plugins
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
```

### 설치한 플러그인 적용
- .zshrc 파일에 추가
```
pligins=(git autojump zsh-autosuggestions zsh-syntax-highlighting)
```

### 터미널 컴퓨터 이름 삭제
- .zshrc 파일에 추가
```
prompt_context() {
    if [[ "$USER" != "$DEFAULT_USER" || -n "$SSH_CLIENT" ]]; then
      prompt_segment black default "%(!.%{%F{yellow}%}.)$USER"
  fi
}
```
### 테마 변경
- .zshrc 파일에 테마 옵션 변경
```
ZSH_THEME="agnoster"
```

- 폰트 설치
```
https://github.com/powerline/fonts/blob/master/SourceCodePro/Source%20Code%20Pro%20for%20Powerline.otf
```

- iterm2 - setting - profile에서 폰트 및 컬러 변경

{% endraw %}
