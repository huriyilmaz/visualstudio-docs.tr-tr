---
title: Git ile çalışma
description: Mac için Visual Studio git 'i kullanma.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: 33148c5202251525504864f26177da4497b5fabe
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983563"
---
# <a name="working-with-git"></a>Git ile çalışma

Git, ekiplerin aynı belgelerde aynı anda çalışmasına izin veren bir dağıtılmış sürüm denetim sistemidir. Bu, tüm dosyaları içeren bir merkezi sunucu olduğu anlamına gelir ancak bir depo bu Merkezi kaynaktan kullanıma alındığı zaman, tüm deponun yerel makineye klonlanmış olması gerekir.

Aşağıdaki bölümler, git 'in Mac için Visual Studio sürüm denetimi için nasıl kullanılabileceğini keşfedebilir.

## <a name="git-version-control-menu"></a>Git sürümü Denetim menüsü

Aşağıdaki görüntüde sürüm denetim menüsü öğesi tarafından Mac için Visual Studio tarafından belirtilen seçenekler gösterilmektedir:

![Sürüm denetimi menü öğesi](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Gönderim ve çekme

Git içinde en sık kullanılan eylemlerden biri gönderiliyor ve çekiliyor. Diğer kişilerin uzak depoya yaptığı değişiklikleri eşleştirmek için Buradan **çekmeniz** gerekir. Bu, **sürüm denetimi > güncelleştirme çözümü**seçilerek Mac için Visual Studio yapılır.

Dosyalarınızı güncelleştirdikten sonra gözden geçirdikten ve kaydettikten sonra başkalarının değişikliklere erişmesine izin vermek **için bunları uzak** depoya göndermeniz gerekir. Bu, **sürüm denetimi > gönderme değişiklikleri**seçilerek Mac için Visual Studio yapılır. Bu, anında Iletme iletişim kutusunu görüntüleyerek, kaydedilen değişiklikleri görüntülemenize ve şu şekilde gönderim yapılacak dalı seçmenizi sağlar:

![Yürütülecek dalı gösteren iletişim kutusu](media/version-control-gitPush.png)

Ayrıca, Kaydet iletişim kutusu aracılığıyla değişikliklerinizi aynı anda kaydedebilir ve gönderebilirsiniz:

![Aynı anda nasıl kayıt yapılacağını ve gönderileceğini gösteren seçenek.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Güçlendirme, günlüğe kaydetme ve birleştirme

Pencerenin alt kısmında, aşağıda gösterildiği gibi beş sekme görüntülenir:

![Sürüm denetimi sekmeleri](media/version-control-gitTabs.png)

Bunlar aşağıdaki eylemlere izin verir:

* **Kaynak** -kaynak kodu dosyanızı görüntüler.
* **Değişiklikler** -yerel dosyanız ve temel dosya arasındaki koddaki değişikliği görüntüler. Ayrıca, farklı karmalardan dosyanın farklı sürümlerini de karşılaştırabilirsiniz:

    ![Değişiklikler sekmesi](media/version-control-gitChange.png)

* **Blame** -her kod bölümüyle ilişkili kullanıcının Kullanıcı adını görüntüler.
* **Günlük** -dosyadan sorumlu tüm işlemeler, saatler, tarihler, iletiler ve kullanıcıları görüntüler:

    ![Günlük sekmesi](media/version-control-gitLog.png)

* **Birleştir** -işinizi kaydederken bir birleştirme çakışması varsa bu kullanılabilir. Siz ve diğer geliştirici tarafından yapılan değişikliklerin görsel bir temsilini gösterir. Bu, her iki kod bölümünü düzgün bir şekilde birleştirmenizi sağlar.

## <a name="switching-branches"></a>Dalları değiştirme

Varsayılan olarak, bir depoda oluşturulan ilk dal, **ana** dal olarak bilinir. Ana dal ile diğeri arasında teknik açıdan farklılık yoktur, ancak ana dal, geliştirme ekiplerinde en sık ' Live ' veya ' üretim ' dalı olarak düşündük.

Bağımsız bir geliştirme hattı, ana öğe (veya başka bir dal) üzerinde dallandırarak oluşturulabilir. Bu, ana dalın zaman içinde yeni bir sürümünü sağlar ve ' canlı ' ' den bağımsız olarak geliştirmeye olanak tanır. Dalları bu şekilde kullanmak, genellikle yazılım geliştirmede özellikler için kullanılır

Kullanıcılar her depo için istedikleri kadar çok dal oluşturabilir, ancak bir dalı kullanmayı bitirdikten sonra depoyu düzenli tutmak üzere silmiş olması önerilir.

Dallar, sürüm denetimine göz atarak Mac için Visual Studio **ve uzak dalları yönetmek > görüntülenir...** :

![Dallar görünümü](media/version-control-gitBranch2.png)

Listede seçip **dala geç** düğmesine basarak başka bir dala geçiş yapın.

Yeni bir dal oluşturmak için Git deposu yapılandırma iletişim kutusunda **Yeni** düğmesini seçin. Yeni dal adını girin:

![Yeni dal oluştur](media/version-control-gitBranch.png)

Ayrıca, _izleme_ dalınıza uzak bir dal ayarlayabilirsiniz. [Git belgelerindeki](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches)dalları izleme hakkında daha fazla bilgi edinin.

Proje adının yanındaki Çözüm Bölmesi geçerli dala bakın:

 ![Geçerli dal çözüm panelinde gösteriliyor](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>İnceleme ve kaydetme

Dosyalardaki değişiklikleri gözden geçirmek için, bu konunun başında gösterildiği gibi, her belge üzerinde yapılan değişiklikleri, güçlendirme 'yi, günlüğü ve birleştirme sekmelerini kullanın.

Sürüm denetimine göz atarak, **çözüm ve COMMIT menü öğesini gözden geçirin >** projenizdeki tüm değişiklikleri gözden geçirin:

![Kod görünümünü gözden geçir](media/version-control-gitReviewCommit.png)

Bu, bir proje dosyasındaki tüm değişikliklerin, alma, düzeltme eki oluşturma veya tamamlama seçeneğiyle görüntülenmesine olanak sağlar.

Uzak depoya bir dosyayı kaydetmek için, **Kaydet**' e basın, bir teslim iletisi girin ve Kaydet düğmesini kullanarak onaylayın:

![Dosya yürütülüyor](media/version-control-gitCommit.png)

Değişikliklerinizi kaydettikten sonra, diğer kullanıcıların bunları görmesine izin vermek için uzak depoya gönderin.

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Ayrıca bkz.

* [Kodunuzu Visual Studio 2017 ve git Azure Repos ile paylaşma](/azure/devops/repos/git/share-your-code-in-git-vs-2017)