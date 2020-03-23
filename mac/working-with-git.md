---
title: Git ile çalışma
description: Mac için Visual Studio'da Git'i kullanma.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: 767c08505877391d71ca085097a0464d516f4f24
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70108019"
---
# <a name="working-with-git"></a>Git ile çalışma

Git, ekiplerin aynı belgeler üzerinde aynı anda çalışmasını sağlayan dağıtılmış bir sürüm kontrol sistemidir. Bu, tüm dosyaları içeren merkezi bir sunucu olduğu anlamına gelir, ancak bir depo bu merkezi kaynaktan kullanıma alındığında, tüm depo yerel makineye klonlanır.

Aşağıdaki bölümlerde Git'in Mac için Visual Studio'da sürüm kontrolü için nasıl kullanılabileceğini inceleyeceğiz.

## <a name="git-version-control-menu"></a>Git sürüm kontrol menüsü

Aşağıdaki resimde, Visual Studio tarafından Mac için Sürüm Denetimi menü öğesi tarafından sağlanan seçenekler gösterilmiştir:

![Sürüm Denetimi menü öğesi](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>İtme ve Çekme

İtme ve Çekme Git içinde en sık kullanılan eylemlerden ikisidir. Diğer kişilerin uzak depoda yaptığı değişiklikleri eşitlemek için oradan **çekmeniz** gerekir. Bu **Sürüm Denetimi > Update Solution**seçerek Mac için Visual Studio yapılır.

Dosyalarınızı güncelleştirip gözden geçirdikten ve işledikten sonra, başkalarının değişikliklerinize erişebilmesi için bunları uzak depoya **itmeniz** gerekir. Bu **Sürüm Denetimi > Push Changes**seçerek Mac için Visual Studio yapılır. Bu, taahhüt edilen değişiklikleri görüntülemenize olanak tanıyan Push iletişim kutusunu görüntüler ve aşağıdakileri yapmak için şubeyi seçer:

![Taahhüt edecek dalı gösteren iletişim kutusu](media/version-control-gitPush.png)

Ayrıca, Commit iletişim kutusu aracılığıyla değişikliklerinizi aynı anda gerçekleştirebilir ve itebilirsiniz:

![Aynı anda nasıl bağlanıp itineceklerini gösteren seçenek.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Suçlama, Günlüğe Kaydetme ve Birleştirme

Pencerenin alt kısmında, aşağıda gösterildiği gibi görüntülenen beş sekme vardır:

![Sürüm Denetimi sekmeleri](media/version-control-gitTabs.png)

Bunlar aşağıdaki eylemlere izin verir:

* **Kaynak** - Kaynak kod dosyanızı görüntüler.
* **Değişiklikler** - Yerel dosyanızla temel dosya arasındaki kod değişikliğini görüntüler. Ayrıca, dosyanın farklı karhes farklı sürümlerikarşılaştırabilirsiniz:

    ![Değişiklikler sekmesi](media/version-control-gitChange.png)

* **Blame** - Kodun her bölümüyle ilişkili kullanıcı adını görüntüler.
* **Günlük** - Dosyadan sorumlu tüm taahhütleri, saatleri, tarihleri, mesajları ve kullanıcıları görüntüler:

    ![Günlük sekmesi](media/version-control-gitLog.png)

* **Birleştirme** - Çalışmanızı işlerken birleştirme çakışması varsa bu kullanılabilir. Sizin ve diğer geliştirici tarafından yapılan değişikliklerin görsel bir gösterimini göstererek kodun her iki bölümünü de temiz bir şekilde birleştirmenizi sağlar.

## <a name="switching-branches"></a>Dalları değiştirme

Varsayılan olarak, bir depoda oluşturulan ilk dal **Ana** dal olarak bilinir. Teknik olarak ana şube ile diğer dal arasında farklı bir şey yoktur, ancak ana dal geliştirme ekiplerinde en sık 'canlı' veya 'üretim' dalı olarak düşünülen daldır.

Master 'ı (veya başka bir dalı) dallandırarak bağımsız bir gelişim çizgisi oluşturulabilir. Bu, zaman içinde bir noktada ana dalanın yeni bir sürümünü sağlar ve 'canlı' olandan bağımsız olarak gelişime olanak sağlar. Dalları bu şekilde kullanmak genellikle yazılım geliştirmedeki özellikler için kullanılır

Kullanıcılar her depo için istedikleri kadar dal oluşturabilir, ancak bir dalı kullanmayı bitirdikten sonra depoyu düzenli tutmak için bu şubenin silinmesi önerilir.

**Şubeler, Sürüm Kontrolü'ne**göz atarak > Şubeleri ve Uzaktan Kumandaları Yöneterek Mac için Visual Studio'da görüntülenir...

![Şubegörünümü](media/version-control-gitBranch2.png)

Listede seçerek ve **Şubeye Geçiş** düğmesine basarak başka bir dala geçin.

Yeni bir dal oluşturmak için Git deposu yapılandırma iletişim kutusunda **Yeni** düğmesini seçin. Yeni şube adını girin:

![Yeni dal oluşturma](media/version-control-gitBranch.png)

İzleme _dalınıza_ uzak bir dal da ayarlayabilirsiniz. [Git belgelerinde](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches)şubeleri izleme hakkında daha fazla bilgi edinin.

Çözüm Defteri'ndeki proje adının yanındaki geçerli dala bakın:

 ![Çözüm defterinde görüntülenen geçerli dal](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>İnceleme ve taahhüt

Dosyalardaki değişiklikleri gözden geçirmek için, bu konuda daha önce gösterildiği her belgede Değişiklikler, Suçlama, Günlük ve Birleştirme sekmelerini kullanın.

Sürüm Denetimi > Gözden Geçir çözüm öğesini inceleyerek projenizdeki tüm değişiklikleri gözden geçirin ve menü öğesini **gerçekleştirin:**

![Kod görünümünü gözden geçirme](media/version-control-gitReviewCommit.png)

Bu, bir projenin her dosyasındaki tüm değişikliklerin Geri Döndürülme, Yama Oluşturma veya Commit seçeneğiyle görüntülenmesini sağlar.

Bir dosyayı uzak depoya işlemek için **Commit**tuşuna basın, bir ileti girin ve Commit Düğmesi ile onaylayın:

![Dosya işleme](media/version-control-gitCommit.png)

Değişikliklerinizi yatırdıktan sonra, diğer kullanıcıların bunları görmesine izin vermek için bunları uzak depoya itin.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Ayrıca bkz.

* [Kodunuzu Visual Studio 2017 ve Azure Repos Git ile paylaşın](/azure/devops/repos/git/share-your-code-in-git-vs-2017)
