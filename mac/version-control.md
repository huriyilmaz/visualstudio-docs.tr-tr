---
title: Sürüm Denetimi
description: Git ve Subversion'ı Mac için Visual Studio.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: f4d5b64e6deeb7952e0d38fce836084399fa2df47153bc3db020db87efa820af
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121437455"
---
# <a name="version-control"></a>Sürüm denetimi

Sürüm denetimi, dosyaları birçok farklı sürümde yönetmek için bir sistemdir ve yazılım geliştirme aşamasında genellikle birçok geliştirici tarafından katkıda bulunabilirsiniz. Herhangi bir sürüm denetim sisteminin _(VCS)_ asıl amacı, tüm kullanıcıların aynı anda kod tabanı üzerinde çalışmasına olanak sağlayan bir çözüm bulmaktır.

Herhangi bir sürüm denetimi sisteminin merkezinde, dosya sunucusuna benzer şekilde tüm farklı dosyalar için merkezi veri deposu olarak hareket ediyor olan bir depo yer almaktadır. Ancak, bir dosya sunucusundan farklı olarak depo, projenin tüm geçmişini ve yapılmış tüm düzeltmeleri içerir.

Depo merkezi veri deposu ise, her kullanıcının yerel bir veri deposuna sahip olup bu veriler üzerinde çalışmasına olanak veren bir mantıksaldır. Bu, çalışma kopyası _olarak adlandırılan bir kopyadır._ Bu Mac için Visual Studio çalışma kopyanız, makinenizin diğer yerel dizinlerinde olduğu gibi görünür ve dosyalardan herhangi birini okumanıza ve dosyalara yazmanıza olanak sağlar. Ancak, Mac için Visual Studio sistemi tümleştirmesi olduğundan, IDE'den ayrılmadan Subversion ve Git kullanabilirsiniz.

Subversion, merkezi bir sürüm denetim sistemidir ve bu da kullanıcıların herhangi bir dosyanın herhangi bir sürümünü kontrol etmek için tüm dosyaları ve düzeltmeleri içeren tek bir sunucu olduğu anlamına gelir. Dosyalar uzak bir Subversion deposundan kullanıma alınarak kullanıma alınarak, kullanıcı deponun o noktada anlık görüntüsünü alır.

Git, ekiplerin aynı belgeler üzerinde aynı anda çalışmasına olanak sağlayan bir dağıtılmış sürüm denetim sistemidir. Git ile tüm dosyaları içeren tek bir sunucu olabilir, ancak bu merkezi kaynaktan bir depo her kullanıma alınmış olduğunda deponun tamamı yerel olarak makinenize kopyalanmış olur.

## <a name="basic-concepts"></a>Temel Kavramlar

Mac için Visual Studio Git ve Subversion sürüm denetimi sistemleri için destek sağlar. Aşağıdaki makalelerde Git ve Subversion depolarının Mac için Visual Studio, ayrıca değişiklikleri gözden geçirme, işleme ve itme gibi basit işlevler keşfedildi.

* [Git Deposu Ayarlama](set-up-git-repository.md)
* [Git ile çalışma](working-with-git.md)
* [Subversion Deposu Ayarlama](set-up-subversion-repository.md)
* [Subversion ile çalışma](working-with-subversion.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio sürüm denetimi (Windows)](/visualstudio/version-control/)