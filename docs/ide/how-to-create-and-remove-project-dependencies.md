---
title: 'Nasıl yapilir: Proje bağımlılıklarını oluşturma ve kaldırma'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114546"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Nasıl yapilir: Proje bağımlılıklarını oluşturma ve kaldırma

Birden çok proje içeren bir çözüm oluştururken, önce belirli projeler oluşturmak, diğer projeler tarafından kullanılan kod oluşturmak için gerekli olabilir. Bir proje başka bir proje tarafından oluşturulan yürütülebilir kodu tüketir, kodu oluşturan proje kodu tüketen projenin proje bağımlılığı olarak adlandırılır. Bu tür bağımlılık ilişkileri **Proje Bağımlılıkları** iletişim kutusunda tanımlanabilir.

## <a name="to-assign-dependencies-to-projects"></a>Projelere bağımlılık atamak için

1. **Çözüm Gezgini'nde**bir proje seçin.

2. **Proje** menüsünde **Proje Bağımlılıkları'nı**seçin.

    **Proje Bağımlılıkları** iletişim kutusu açılır.

   > [!NOTE]
   > **Proje Bağımlılıkları** seçeneği yalnızca birden fazla projeiçeren bir çözümde kullanılabilir.

3. **Bağımlılıklar** sekmesinde, **Proje** açılır menüsünden bir proje seçin.

4. Alana **Bağlı Olarak,** bu projeden önce oluşturulması gereken diğer herhangi bir projenin onay kutusunu seçin.

   Proje bağımlılıkları oluşturabiliyor olmak için çözümünuzun birden fazla projeden oluşması gerekir.

## <a name="to-remove-dependencies-from-projects"></a>Projelerdeki bağımlılıkları kaldırmak için

1. **Çözüm Gezgini'nde**bir proje seçin.

2. **Proje** menüsünde **Proje Bağımlılıkları'nı**seçin.

     **Proje Bağımlılıkları** iletişim kutusu açılır.

    > [!NOTE]
    > **Proje Bağımlılıkları** seçeneği yalnızca birden fazla projeiçeren bir çözümde kullanılabilir.

3. **Bağımlılıklar** sekmesinde, **Proje** açılır menüsünden bir proje seçin.

4. Alana **Bağlı** olarak, artık bu projenin bağımlılığı olmayan diğer projelerin yanındaki onay kutularını temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da projeler ve çözümler oluşturun ve temizleyin](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
