---
title: Sürüm Denetimi
description: Mac için Visual Studio Git ve alt sürüm kullanma.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 2ae148de845e916542c4b1c43a177e23104fb8af
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805019"
---
# <a name="version-control"></a>Sürüm denetimi

Sürüm denetimi, birçok farklı sürümde dosya yönetmeye yönelik bir sistemdir ve yazılım geliştirme ' de genellikle birçok geliştirici tarafından katkıda bulunur. Herhangi bir sürüm denetim sisteminin (_VCS_) asıl amacı, tüm kullanıcıların kod temeli üzerinde aynı anda çalışmasını sağlayan bir çözüm buladır.

Herhangi bir sürüm denetim sisteminin çekirdeğine, bir dosya sunucusuna benzer şekilde, tüm farklı dosyalar için merkezi veri deposu görevi gören bir _depodur_. Bununla birlikte, bir dosya sunucusunun aksine depo, projenin tüm geçmişini ve yapılan tüm düzeltmeleri içerir.

Depo Merkezi veri deposunuysa, her bir kullanıcının verilerin yerel bir deposuna sahip olması ve üzerinde çalışmasına izin verilmesi gerekir. Buna _çalışma kopyası_ denir. Mac için Visual Studio çalışma kopyanız, makinenizde herhangi bir yerel dizin gibi görünür, böylece herhangi bir dosyayı okuyup yazabilir. ancak, Mac için Visual Studio sürüm denetimi sistem tümleştirmesi olduğundan, ıde 'den çıkmadan alt sürüm ve Git 'i kullanabilirsiniz.

Alt sürüm merkezi bir sürüm denetim sistemidir. Bu, kullanıcıların herhangi bir dosyanın herhangi bir sürümünü denetleyebileceği tüm dosya ve düzeltmeleri içeren tek bir sunucu olduğu anlamına gelir. Dosyalar uzak bir alt sürüm deposundan kullanıma alındığı zaman, Kullanıcı o anda deponun anlık görüntüsünü alır.

Git, ekiplerin aynı belgelerde aynı anda çalışmasına izin veren bir dağıtılmış sürüm denetim sistemidir. Git ile tüm dosyaları içeren tek bir sunucu olabilir, ancak bu Merkezi kaynaktan bir depo kullanıma alındığı zaman tüm deponun makinenize yerel olarak klonlanmış olması gerekir.

## <a name="basic-concepts"></a>Temel Kavramlar

Mac için Visual Studio hem Git hem de alt sürüm denetim sistemleri için destek sağlar. aşağıdaki makalelerde Git ve alt sürüm depolarının Mac için Visual Studio aracılığıyla ayarlanması ve değişiklikleri gözden geçirme, yürütme ve gönderme gibi basit işlevsellikler de araştırmaktadır.

* [Git Deposu Ayarlama](set-up-git-repository.md)
* [Git ile çalışma](working-with-git.md)
* [Subversion Deposu Ayarlama](set-up-subversion-repository.md)
* [Subversion ile çalışma](working-with-subversion.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio sürüm denetimi (Windows)](/visualstudio/version-control/)