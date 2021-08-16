---
title: Git ile çalışma
description: Git'i Mac için Visual Studio.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: ed9e93eeca9f4c1fc3a5d130948a18741f99e0ec0ee58910c59268dc4002ab8a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121382316"
---
# <a name="working-with-git"></a>Git ile çalışma

Git, ekiplerin aynı belgeler üzerinde aynı anda çalışmasına olanak sağlayan bir dağıtılmış sürüm denetim sistemidir. Bu, tüm dosyaları içeren bir merkezi sunucu olduğu anlamına gelir, ancak bu merkezi kaynaktan bir depo kullanıma alınmışsa, deponun tamamı yerel makineye kopyalanmış olur.

Aşağıdaki bölümlerde Git'in bu sürümlerde sürüm denetimi için nasıl Mac için Visual Studio.

## <a name="git-version-control-menu"></a>Git sürüm denetimi menüsü

Aşağıdaki resimde, Sürüm Denetimi menü öğesi Mac için Visual Studio tarafından sağlanan seçenekler gösterilmiştir:

![Sürüm Denetimi menü öğesi](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Itme ve Çekme

Itme ve Çekme, Git içinde en sık kullanılan eylemlerden ikisidir. Diğer kişilerin uzak depoda yaptığı değişiklikleri eşitlemek için buradan **çekmeniz** gerekir. Bu, Güncelleştirme Mac için Visual Studio sürüm denetimi **seçerek > yapılır.**

Dosyalarınızı güncelleştirmenizin, gözden geçirmenizin ve işlemenizin  ardından başkalarının değişikliklerinize erişmesine izin vermek için bunları uzak depoya itmeniz gerekir. Bu, değişiklikleri Mac için Visual Studio Için Sürüm **Denetimi seçerek > yapılır.** Bu, kaydedilmiş değişiklikleri görüntülemenizi ve itmek istediğiniz dalı seçmenizi sağlayan Push iletişim kutusunu görüntüler:

![Işlemek için dal gösteren iletişim kutusu](media/version-control-gitPush.png)

Ayrıca, Commit (Yürütme) iletişim kutusu aracılığıyla değişikliklerinizi aynı anda Işle ve Gönder'i de kullanabilirsiniz:

![Aynı anda işleme ve itme seçeneğini gösteren seçenek.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Blame, Log ve Merge

Pencerenin alt kısmında, aşağıda gösterildiği gibi beş sekme görüntülenir:

![Sürüm Denetimi sekmeleri](media/version-control-gitTabs.png)

Bunlar aşağıdaki eylemlere olanak sağlar:

* **Kaynak** - Kaynak kod dosyanızı görüntüler.
* **Değişiklikler** - Yerel dosyanız ile temel dosya arasındaki kodda yapılan değişikliği görüntüler. Dosyanın farklı sürümlerini farklı karmalardan da karşılaştırabilirsiniz:

    ![Değişiklikler sekmesi](media/version-control-gitChange.png)

* **Blame** - Kodun her bölümüyle ilişkili kullanıcının kullanıcı adını görüntüler.
* **Günlük** - Dosyadan sorumlu olan tüm işlemeleri, saatleri, tarihleri, iletileri ve kullanıcıları görüntüler:

    ![Günlük sekmesi](media/version-control-gitLog.png)

* **Birleştirme** - Bu, çalışmanızı işlerken birleştirme çakışması varsa kullanılabilir. Siz ve diğer geliştirici tarafından yapılan değişikliklerin görsel bir gösterimini gösterir ve her iki kod bölümlerini de temiz bir şekilde birleştirmeye olanak sağlar.

## <a name="switching-branches"></a>Dalları değiştirme

Varsayılan olarak, bir depoda oluşturulan ilk dal ana dal **olarak** bilinir. Ana dalla diğer dal arasında teknik açıdan farklı bir şey yok ancak ana dal, geliştirme ekiplerinin 'canlı' veya 'üretim' dalı olarak en sık olarak değerlendiren dalıdır.

Ana daldan (veya başka bir daldan) bağımsız bir geliştirme hattı oluşturulabilir. Bu, ana dalın belirli bir noktada yeni bir sürümünü sağlayarak "canlı" daldan bağımsız olarak geliştirme sağlar. Dalların bu şekilde kullanımı genellikle yazılım geliştirme özellikleri için kullanılır

Kullanıcılar her depo için en fazla sayıda dal oluşturabilir, ancak bir dal kullanmayı bitirdikten sonra depoyu düzenli tutmak için bu dalların silinmesi önerilir.

Dallar, Dalları Mac için Visual Studio Uzak Dalları Yönet... > **Denetimi'ne göz atarak bu görünüme sahiptir:**

![Dallar görünümü](media/version-control-gitBranch2.png)

Listeden seçerek ve Dala Geç düğmesine basarak başka bir **dala geçiş** yapmak.

Yeni bir dal oluşturmak için Git **deposu** yapılandırma iletişim kutusunda Yeni düğmesini seçin. Yeni dal adını girin:

![Yeni dal oluşturma](media/version-control-gitBranch.png)

Bir uzak dalı izleme dalınıza da _ayarlayın._ Git belgelerinde dalları izleme hakkında daha [fazla bilgi edinin.](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches)

Proje adının yanındaki Çözüm Bölmesi geçerli dala bakın:

 ![Çözüm paneli içinde görüntülenen geçerli dal](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Gözden geçirme ve işleme

Dosyalarda yapılan değişiklikleri gözden geçirmek için, bu konunun önceki sürümlerinde gösterildiği gibi her bir belgede Değişiklikler, Sorumlu, Günlük ve Birleştir sekmelerini kullanın.

Sürüm Denetimi'ne göz atarak projenizin tüm **değişikliklerini** gözden > Ve Commit menü öğesini gözden geçirebilirsiniz:

![Kod görünümünü gözden geçirme](media/version-control-gitReviewCommit.png)

Bu, projenin her dosyasındaki tüm değişikliklerin Geri Döndürme, Düzeltme Eki Oluşturma veya Yürütme seçeneğiyle görüntülemesini sağlar.

Bir dosyayı uzak depoya işlemek için, Commit tuşuna **basın,** bir işleme iletisi girin ve Commit Düğmesi ile onaylayın:

![Dosya işleme](media/version-control-gitCommit.png)

Değişikliklerinizi işleyip diğer kullanıcıların bunları görmelerini sağlayacak şekilde uzak depoya itin.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Ayrıca bkz.

* [Kodunuzu Visual Studio 2017 ve Git ile Azure Repos paylaşma](/azure/devops/repos/git/share-your-code-in-git-vs-2017)