# Configuracao Sublime - LSP

# 1. Instalar o ccls

Você pode instalar o ccls usando o Homebrew, que é um gerenciador de pacotes popular para macOS:

```sh
brew install ccls
```

# Configurar o LSP no Sublime Text
Abra as configurações do LSP no Sublime Text e adicione a configuração para ccls:

1. Vá para `Preferences` > `Package Settings` > `LSP` > `Settings`.
2. Adicione a configuração para ccls:
```json
{
    "clients": {
        "ccls": {
            "command": ["ccls"],
            "selector": "source.c++, source.c, source.cpp",
            "initializationOptions": {
                "cache": {
                    "directory": "/path/to/cache"   // ~/Library/Caches/ccls
                }
            }
        }
    }
}

```
Certifique-se de substituir `/path/to/cache` por um caminho válido onde o ccls possa armazenar arquivos em cache.

# 3. Verificar a Configuração do Projeto
> [!NOTE]
> Para garantir que o ccls funcione corretamente com o Sublime Text e reconheça erros em qualquer arquivo C++, você precisará criar um projeto na pasta desejada e adicionar as configurações específicas ao arquivo do projeto.


```json
{
    "folders":
    [
        {
            "path": "."    // Aqui pode ser o caminho raiz da sua pasta, desde que crie o projeto aqui também...
        }
    ],
    "settings": {
        "LSP": {
            "ccls": {
                "command": ["ccls"],
                "enabled": true
            }
        }
    }
}
```

# 4. Verificar se o Arquivo está Sendo Reconhecido
Certifique-se de que o arquivo C++ está sendo reconhecido pelo LSP. O arquivo deve ter a extensão correta (.cpp, .hpp, .c, .h) e você deve ver o servidor de linguagem sendo iniciado na barra de status do Sublime Text.

# 5. Verificar a Janela de Diagnósticos
Abra a janela de diagnósticos do LSP:

1. Vá para `Tools` > `LSP` > `Diagnostics Panel`.
2. Verifique se há alguma mensagem de erro ou diagnóstico na janela.

# 6. Verificar os Logs do LSP
Às vezes, verificar os logs pode ajudar a identificar o problema. Abra o painel de logs:

Vá para `View` > `Show Console`.
Verifique se há alguma mensagem de erro ou aviso relacionada ao LSP.

# 7. Verificar a Configuração do Sistema de Build
Certifique-se de que o sistema de build do C++ esteja configurado corretamente no Sublime Text:

1. Vá para `Tools` > `Build System`.
2. Selecione um sistema de build apropriado para C++ (por exemplo, `C++`).

# Exemplo de Configuração Completa
Aqui está um exemplo completo, considerando que você está usando `ccls` como o servidor de linguagem:

Arquivo de Configuração do LSP (`LSP.sublime-settings`)

```json
{
    "clients": {
        "ccls": {
            "command": ["ccls"],
            "selector": "source.c++, source.c",
            "initializationOptions": {
                "cache": {
                    "directory": "~/Library/Caches/ccls"
                }
            }
        }
    }
}
```
Arquivo de Projeto (`Project.sublime-project`)
```json
{
    "folders":
    [
        {
            "path": "."
        }
    ],
    "settings": {
        "LSP": {
            "ccls": {
                "command": ["ccls"],
                "enabled": true
            }
        }
    }
}
```
# 8. Reinstalar o LSP e o Cliente C++
Se tudo mais falhar, tente reinstalar o pacote LSP e o cliente C++ no Sublime Text.

## Resumo
Certifique-se de que `ccls` está instalado usando o Homebrew.
Configure o `LSP` corretamente no Sublime Text.
Verifique se os arquivos C++ estão sendo reconhecidos.
Abra e verifique a janela de diagnósticos.
Verifique os logs do LSP.
Reinstale o LSP e o cliente C++ se necessário.
Se após todas essas etapas o problema persistir, pode haver um problema específico de ambiente ou configuração que necessite de uma investigação mais detalhada.

> [!IMPORTANT]
> Para configurar corretamente o SublimeLinter no Sublime Text, é essencial seguir as instruções detalhadas no arquivo `Install.md`.
> Este documento contém passos cruciais que garantem o funcionamento adequado do SublimeLinter.

> [!TIP]
> Esta configuração está funcionando perfeitamente e sem erros, conforme indicado pela funcionalidade atual dos pacotes e ferramentas listadas acima.


