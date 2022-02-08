---
title: Visual Studio uzak dala gönder
titleSuffix: ''
description: GitHub veya Azure DevOps kullanarak Visual Studio uzak bir uzaktan gönderin.
ms.date: 11/10/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
---
# <a name="push-from-visual-studio-to-a-remote-branch"></a>Visual Studio 'den uzak dala gönderim 

GitHub kimlik doğrulamasından geçtikten sonra, Visual Studio GitHub iş akışınızı iyileştirebilirler. bu geliştirmelerden biri, yerel bir projeyi tek bir tıklamayla GitHub düz olarak (yayımlama olarak da bilinir) gönderme yeteneğidir. Basit bir git iş akışındaki son aşama, değişiklikleri uzak uygulamanıza göndermaktır.

Uzak bir, kodunuzun buluta depolanması için güvenli bir yerdir. Genellikle **Origin/Main** (veya Origin/Master) olarak adlandırılır; burada "Origin" uzak için varsayılan addır. Bu terminoloji hakkında daha fazla bilgi için git Web sitesindeki [Git Dallanma-uzak dallar](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches) sayfasına bakın.

bu makale GitHub depolarına başvurduğundan, GitHub, GitLab veya Azure DevOps gibi tercih ettiğiniz Git sağlayıcısıyla uzaktan çalışabilirsiniz. 

Visual Studio ' de uzak bir uzaktan nasıl gönderirsiniz.

1. Daha önce [oluşturulmuş](git-create-repository.md) veya [kopyalanmış](git-clone-repository.md) depoda üzerinde çalışmak üzere bir dosyanın açık olduğundan emin olun.

1. Dosyada bir değişiklik yapın, kaydedin, **Git değişiklikler** sekmesini seçin ve ardından değişikliği [uygulayın](git-make-commit.md) .

1. **Git değişiklikleri** penceresinde gelen ve giden işleme sayısını içeren bağlantı metnine dikkat edin. Aşağıdaki örnekte, bağlantı metni **gelen 1 giden/0**' ı okur.

   :::image type="content" source="media/vs-2022/git-changes-window-outgoing-incoming.png" alt-text="Git, Visual Studio 2022 ' de vurgulanan giden/gelen bağlantı metniyle birlikte değişir.":::

   "Giden" metin, henüz uzaktan gönderilmemiş olan işlemelerin sayısını temsil eder, "gelen" metin, getirilen ancak henüz uzak olmayan işlemeleri temsil eder.

1. Uzaktan göndermek için, **Gönder** düğmesini seçin veya **Git** menüsünden **Gönder** ' i seçin.

## <a name="next-steps"></a>Sonraki adımlar

yolculuğa devam etmek için [Visual Studio getirme, çekme ve eşitleme](git-fetch-pull-sync.md) ' yi ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Git deneyimi Visual Studio](git-with-visual-studio.md)
- [Visual Studio & GitHub: birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
