---
title: Sürüm Denetimi
description: Mac için Visual Studio'da Git ve Subversion'u kullanma.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 47b51306f8d0916eccd7db3a4740843bb7efba85
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984735"
---
# <a name="version-control"></a>Sürüm denetimi

Sürüm denetimi, birçok farklı sürüm üzerinden dosya yönetimi için bir sistemdir ve - yazılım geliştirmede - genellikle birçok geliştirici tarafından katkıda bulunulan bir sistemdir. Herhangi bir sürüm kontrol sisteminin _(VCS)_ temel amacı, tüm kullanıcıların kod tabanı üzerinde aynı anda çalışmasını sağlayan bir çözüm bulmaktır.

Herhangi bir sürüm kontrol sisteminin özünde bir _depo_, tüm farklı dosyalar için merkezi veri deposu olarak hareket eder - bir dosya sunucusuna benzer. Ancak, bir dosya sunucusunun aksine, depo projenin tüm geçmişini ve yapılan tüm düzeltmeleri içerir.

Depo merkezi veri deposuysa, her kullanıcının verilerin yerel bir deposuna sahip olması ve bu da üzerinde çalışmalarına olanak sağlar. Buna çalışan _kopya_denir. Mac için Visual Studio'da çalışan kopyanız, makinenizdeki diğer yerel dizinler gibi görünür ve dosyalardan herhangi birini okumanızı ve yazmanızı sağlar. Ancak, Mac için Visual Studio Sürüm denetim sistemi entegrasyonu na sahip olduğundan, IDE'den ayrılmadan Subversion ve Git'i kullanabilirsiniz.

Subversion merkezi bir sürüm kontrol sistemi, hangi kullanıcıların herhangi bir dosyanın herhangi bir sürümünü kontrol edebilirsiniz tüm dosyaları ve düzeltmeleri içeren tek bir sunucu olduğu anlamına gelir. Dosyalar uzak bir Subversion deposundan kullanıma alındığında, kullanıcı o anda deponun anlık görüntüsünü alır.

Git, ekiplerin aynı belgeler üzerinde aynı anda çalışmasını sağlayan dağıtılmış bir sürüm kontrol sistemidir. Git ile tüm dosyaları içeren tek bir sunucu olabilir, ancak bu merkezi kaynaktan bir depo kullanıma alındığında tüm depo yerel olarak makinenize klonlanır.

## <a name="basic-concepts"></a>Temel Kavramlar

Mac için Visual Studio hem Git hem de Subversion sürüm kontrol sistemleri için destek sağlar. Aşağıdaki makaleler, Mac için Visual Studio aracılığıyla Git ve Subversion depoları kurmanın yanı sıra değişiklikleri gözden geçirme, taahhüt etme ve zorlama gibi basit işlevleri de inceler.

* [Git Deposu Ayarlama](set-up-git-repository.md)
* [Git ile çalışma](working-with-git.md)
* [Subversion Deposu Ayarlama](set-up-subversion-repository.md)
* [Subversion ile çalışma](working-with-subversion.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'da sürüm denetimi (Windows'da)](/visualstudio/version-control/)