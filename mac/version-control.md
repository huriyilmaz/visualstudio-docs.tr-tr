---
title: Sürüm Denetimi
description: Mac için Visual Studio git ve alt sürüm kullanma.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 9206ab892ef125706ab16f9a739fe88a52f5c242
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "70108107"
---
# <a name="version-control"></a>Sürüm denetimi

Sürüm denetimi, birçok farklı sürümde dosya yönetmeye yönelik bir sistemdir ve yazılım geliştirme ' de genellikle birçok geliştirici tarafından katkıda bulunur. Herhangi bir sürüm denetim sisteminin (_VCS_) asıl amacı, tüm kullanıcıların kod temeli üzerinde aynı anda çalışmasını sağlayan bir çözüm buladır.

Herhangi bir sürüm denetim sisteminin çekirdeğine, bir dosya sunucusuna benzer şekilde, tüm farklı dosyalar için merkezi veri deposu görevi gören bir _depodur_. Bununla birlikte, bir dosya sunucusunun aksine depo, projenin tüm geçmişini ve yapılan tüm düzeltmeleri içerir.

Depo Merkezi veri deposunuysa, her bir kullanıcının verilerin yerel bir deposuna sahip olması ve üzerinde çalışmasına izin verilmesi gerekir. Buna _çalışma kopyası_denir. Mac için Visual Studio çalışma kopyanız, makinenizde herhangi bir yerel dizin gibi görünür, böylece herhangi bir dosyayı okuyup yazabilir. Ancak, Mac için Visual Studio sürüm denetimi sistem tümleştirmesi olduğundan, IDE 'den çıkmadan alt sürüm ve git 'i kullanabilirsiniz.

Alt sürüm merkezi bir sürüm denetim sistemidir. Bu, kullanıcıların herhangi bir dosyanın herhangi bir sürümünü denetleyebileceği tüm dosya ve düzeltmeleri içeren tek bir sunucu olduğu anlamına gelir. Dosyalar uzak bir alt sürüm deposundan kullanıma alındığı zaman, Kullanıcı o anda deponun anlık görüntüsünü alır.

Git, ekiplerin aynı belgelerde aynı anda çalışmasına izin veren bir dağıtılmış sürüm denetim sistemidir. Git ile tüm dosyaları içeren tek bir sunucu olabilir, ancak bu Merkezi kaynaktan bir depo kullanıma alındığı zaman tüm deponun makinenize yerel olarak klonlanmış olması gerekir.

## <a name="basic-concepts"></a>Temel Kavramlar

Mac için Visual Studio hem git hem de alt sürüm denetim sistemleri için destek sağlar. Aşağıdaki makalelerde git ve alt sürüm depolarının Mac için Visual Studio aracılığıyla ayarlanması ve değişiklikleri gözden geçirme, yürütme ve gönderme gibi basit işlevsellikler de araştırmaktadır.

* [Git Deposu Ayarlama](set-up-git-repository.md)
* [Git ile çalışma](working-with-git.md)
* [Subversion Deposu Ayarlama](set-up-subversion-repository.md)
* [Subversion ile çalışma](working-with-subversion.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 'da sürüm denetimi (Windows üzerinde)](/visualstudio/version-control/)