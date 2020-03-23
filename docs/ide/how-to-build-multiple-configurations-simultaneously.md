---
title: 'Nasıl yapılı: Aynı anda birden çok yapılandırma oluşturma'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cd217a08f62b4919af6d72017176c110cf5e5a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904093"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Nasıl yapılı: Aynı anda birden çok yapılandırma oluşturma

**Toplu Yapı** iletişim kutusunu kullanarak, yapı yapılandırmalarının çoğu veya tümü aynı anda birçok projeye sahip olabilir. Ancak, aynı anda birden çok yapı yapılandırmasında aşağıdaki proje türlerini oluşturamazsınız:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]JavaScript kullanarak Windows için oluşturulmuş uygulamalar.

2. Tüm Visual Basic projeleri.

Bir çözüm bu iki proje türünden herhangi bir proje içeriyorsa, **Toplu Yapı** bu çözüm için kullanılamaz. Bu durumda, komut **Yapı** menüsünde görünmez.

   Yapı yapılandırmaları hakkında daha fazla bilgi için [bkz.](../ide/understanding-build-configurations.md)

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Birden çok yapı yapılandırmasında proje oluşturmak için

1. Menü çubuğunda **Toplu Oluştur Oluştur'u** > **Batch Build**seçin. Veya arama kutusunu açmak için **Ctrl**+**Q** `Batch Build`tuşuna basın ve .

2. **Yapı** sütununda, proje oluşturmak istediğiniz yapılandırmalar için onay kutularını seçin.

    > [!TIP]
    > Bir çözüm için yapı yapılandırmasını düzenleme veya oluşturmak için, **Configuration Manager** iletişim kutusunu açmak için menü çubuğunda Yapı**Yapılandırma Yöneticisi'ni** **seçin.** >  Bir çözüm için yapı yapılandırması düzenledikten sonra, çözümdeki projelerin tüm yapı yapılandırmalarını güncelleştirmek için **Toplu Oluşturma** iletişim kutusundaki **Yeniden Oluştur** düğmesini seçin.

3. Belirttiğiniz yapılandırmalarla projeyi oluşturmak için **Oluştur** veya **Oluştur** düğmelerini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılı: Yapılandırmalar oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)