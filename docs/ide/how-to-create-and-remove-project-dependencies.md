---
title: 'Nasıl yapılır: Proje bağımlılıklarını oluşturma ve kaldırma'
ms.date: 06/21/2017
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
ms.technology: vs-ide-compile
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a286a84d01c6a49b32445106488688ba5b489be
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114546"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Nasıl yapılır: Proje bağımlılıklarını oluşturma ve kaldırma

Birden fazla proje içeren bir çözüm oluştururken, diğer projeler tarafından kullanılan kodu oluşturmak için önce belirli projeleri oluşturmak gerekebilir. Bir proje, başka bir proje tarafından oluşturulan yürütülebilir kodu kullandığında, kodu üreten proje, kodu tüketen projenin bir proje bağımlılığı olarak adlandırılır. Bu tür bağımlılık ilişkileri **Proje bağımlılıkları** iletişim kutusunda tanımlanabilir.

## <a name="to-assign-dependencies-to-projects"></a>Projelere bağımlılıklar atamak için

1. **Çözüm Gezgini**bir proje seçin.

2. **Proje** menüsünde **Proje bağımlılıkları**' nı seçin.

    **Proje bağımlılıkları** iletişim kutusu açılır.

   > [!NOTE]
   > **Proje bağımlılıkları** seçeneği yalnızca birden fazla proje içeren bir çözümde kullanılabilir.

3. **Bağımlılıklar** sekmesinde, **Proje** açılan menüsünden bir proje seçin.

4. **Bağlı** alanında, bu proje öncesinde oluşturulması gereken başka bir projenin onay kutusunu seçin.

   Proje bağımlılıklarını oluşturabilmeniz için Çözümünüzün birden fazla projeden oluşması gerekir.

## <a name="to-remove-dependencies-from-projects"></a>Projelerden bağımlılıkları kaldırmak için

1. **Çözüm Gezgini**bir proje seçin.

2. **Proje** menüsünde **Proje bağımlılıkları**' nı seçin.

     **Proje bağımlılıkları** iletişim kutusu açılır.

    > [!NOTE]
    > **Proje bağımlılıkları** seçeneği yalnızca birden fazla proje içeren bir çözümde kullanılabilir.

3. **Bağımlılıklar** sekmesinde, **Proje** açılan menüsünden bir proje seçin.

4. **Bağlı** alanında, bu projenin artık bağımlılıkları olmayan diğer projelerin yanındaki onay kutularını temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da projeler ve çözümler oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
