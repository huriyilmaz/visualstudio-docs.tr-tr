---
title: Visual Studio'de uzak bir dala Visual Studio
titleSuffix: ''
description: Git veya Visual Studio kullanarak bir uzak depoya Azure DevOps.
ms.date: 11/10/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8cd806a335db0f00d5ff381c92505c7085aa59fa
ms.sourcegitcommit: 204973a0fde6c1dbe1e8fd6e1d2483bc1b7873ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "138000370"
---
# <a name="push-from-visual-studio-to-a-remote-branch-in-github"></a>Bir Visual Studio uzak dala GitHub

Kimlik doğrulaması tamamlandıktan sonra GitHub Visual Studio iş akışınızı GitHub edebilirsiniz. Bu geliştirmelerden biri, yerel bir projeyi tek tıklamayla doğrudan yerel bir projeye GitHub (yayımlama olarak da bilinir) özelliğidir. Basit bir Git iş akışının son aşaması, değişiklikleri uzak depoya itmektir.

Uzak depo, kodunuzu bulutta depolamak için güvenli bir yerdir. Genellikle origin **/main (veya origin/** master) olarak adlandırılır; burada "origin" uzak için varsayılan addır. Bu terminoloji hakkında daha fazla bilgi için Git web sitesinin [Git Dallama - Uzak](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches) Dallar sayfasına bakın.

Burada, bir uzak sunucuya uzak sunucuya nasıl Visual Studio.

1. Daha önce oluşturulmuş veya kopyalanmış bir repoda üzerinde çalışmak için açık [bir dosyanız](git-create-repository.md) [olduğundan emin](git-clone-repository.md) olun.

1. Dosyada bir değişiklik yapın, dosyayı kaydedin, **Git Değişiklikleri sekmesini** seçin ve ardından [değişikliği](git-make-commit.md) işleyebilirsiniz.

1. **Git Değişiklikleri penceresinde**, gelen ve giden işlemelerin sayısını içeren bağlantı metnine dikkat edin. Aşağıdaki örnekte, bağlantı metni **1 giden / 0 geleni okur**.

   :::image type="content" source="media/vs-2022/git-changes-window-outgoing-incoming.png" alt-text="2022'de giden/gelen bağlantı metninin vurgulanmış olduğu Git Visual Studio penceresi.":::

   "Giden" metin henüz uzak bilgisayara gönderilemeyen işleme sayısını, "gelen" metin ise getirilmiş ancak henüz uzaktan çekilemeyen işlemeleri temsil eder.

1. Uzak depoya itmek için, Düğmeye **bas'ı** seçin veya Git **menüsünden** **Anındat'ı** seçin.

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için Giriş [sayfasındaki Fetch, pull ve sync Visual Studio](git-fetch-pull-sync.md) ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de Git deneyimi](git-with-visual-studio.md)
- [Visual Studio & GitHub: Birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
