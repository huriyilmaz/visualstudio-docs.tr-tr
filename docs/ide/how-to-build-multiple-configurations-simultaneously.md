---
title: 'Nasıl yapılır: aynı anda birden fazla yapılandırma derleme'
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
ms.sourcegitcommit: b016ea260856264eee730ee8cbcab198314a7ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77904093"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Nasıl yapılır: aynı anda birden fazla yapılandırma derleme

**Toplu Iş oluşturma** iletişim kutusunu kullanarak, aynı anda birden çok proje türünü, yapı yapılandırmalarının birden çok kez veya hatta tamamını oluşturabilirsiniz. Ancak, aynı anda birden çok yapı yapılandırmasında aşağıdaki proje türlerini derleyebilirsiniz:

1. JavaScript kullanarak Windows için oluşturulmuş uygulamalar [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)].

2. Tüm Visual Basic projeleri.

Bir çözüm bu iki proje türünün herhangi bir projesini içeriyorsa, **Toplu derleme** bu çözüm için kullanılamaz. Bu durumda, komut **Build** menüsünde görünmez.

   Derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Birden çok yapı yapılandırmasında bir proje oluşturmak için

1. Menü çubuğunda, **Toplu derleme** > **Oluştur** ' u seçin. Ya da, ara kutusunu açmak için **Ctrl**+**Q** tuşlarına basın ve `Batch Build`aratın.

2. **Build** sütununda, bir proje derlemek istediğiniz yapılandırmaların onay kutularını seçin.

    > [!TIP]
    > Bir çözüme yönelik derleme yapılandırması düzenlemek veya oluşturmak için, menü çubuğunda **Configuration Manager** > **Oluştur** ' u seçerek **Configuration Manager** iletişim kutusunu açın. Bir çözüm için yapı yapılandırmasını düzenledikten sonra, çözümdeki projelerin tüm derleme yapılandırmalarını güncelleştirmek için **Batch derlemesi** Iletişim kutusundaki **yeniden oluştur** düğmesini seçin.

3. Projeyi belirttiğiniz yapılandırmalara göre derlemek için **Derle** veya **yeniden oluştur** düğmelerini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
- [Derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md)
- [Paralel olarak birden çok proje oluşturun](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)