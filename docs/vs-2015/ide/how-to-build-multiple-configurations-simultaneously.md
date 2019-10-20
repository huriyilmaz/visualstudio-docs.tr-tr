---
title: 'Nasıl yapılır: aynı anda birden çok yapılandırma oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 719b31e834b5410dd137a0c5b69cc07ae01651e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645467"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Nasıl yapılır: Aynı Anda Birden Fazla Yapılandırma Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Toplu Iş oluşturma** iletişim kutusunu kullanarak, aynı anda birden çok proje türünü, yapı yapılandırmalarının birden çok kez veya hatta tamamını oluşturabilirsiniz. Ancak, aynı anda birden çok yapı yapılandırmasında aşağıdaki proje türlerini derleyebilirsiniz:

1. JavaScript kullanarak Windows için oluşturulmuş uygulamalar [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)].

2. Tüm Visual Basic projeleri.

   Derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).

### <a name="to-build-a-project-in-multiple-build-configurations"></a>Birden çok yapı yapılandırmasında bir proje oluşturmak için

1. Menü çubuğunda **Oluştur**, **toplu iş oluştur**' u seçin.

2. **Build** sütununda, bir proje derlemek istediğiniz yapılandırmaların onay kutularını seçin.

    > [!TIP]
    > Bir çözüme yönelik yapı yapılandırması düzenlemek veya oluşturmak için, **Configuration Manager** iletişim kutusunu açmak için, menü çubuğunda **Oluştur**, **Configuration Manager** öğesini seçin. Bir çözüm için yapı yapılandırmasını düzenledikten sonra, çözümdeki projelerin tüm derleme yapılandırmalarını güncelleştirmek için **Batch derlemesi** Iletişim kutusundaki **yeniden oluştur** düğmesini seçin.

3. Projeyi belirttiğiniz yapılandırmalara göre derlemek için **Derle** veya **yeniden oluştur** düğmelerini seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md) yapılandırma [yapılandırma yapılandırma,](../ide/understanding-build-configurations.md) [paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
