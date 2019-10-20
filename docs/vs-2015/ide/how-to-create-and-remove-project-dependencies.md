---
title: 'Nasıl yapılır: Proje bağımlılıklarını oluşturma ve kaldırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1403beccdb6bf9b938787f62cb3da2e5bb5c259
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668128"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Nasıl Yapılır: Proje Bağımlılıklarını Oluşturma ve Kaldırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birden fazla proje içeren bir çözüm oluştururken, diğer projeler tarafından kullanılan kodu oluşturmak için önce belirli projeleri oluşturmak gerekebilir. Bir proje, başka bir proje tarafından oluşturulan yürütülebilir kodu kullandığında, kodu üreten proje, kodu tüketen projenin bir proje bağımlılığı olarak adlandırılır. Bu tür bağımlılık ilişkileri **Proje bağımlılıkları** iletişim kutusunda tanımlanabilir.

### <a name="to-assign-dependencies-to-projects"></a>Projelere bağımlılıklar atamak için

1. Çözüm Gezgini bir proje seçin.

2. **Proje** menüsünde **Proje bağımlılıkları**' nı seçin.

    **Proje bağımlılıkları** iletişim kutusu açılır.

   > [!NOTE]
   > **Proje bağımlılıkları** seçeneği yalnızca birden fazla proje içeren bir çözümde kullanılabilir.

3. **Bağımlılıklar** sekmesinde, **Proje** açılan menüsünden bir proje seçin.

4. **Bağlı** alanında, bu proje öncesinde oluşturulması gereken başka bir projenin onay kutusunu seçin.

   Proje bağımlılıklarını oluşturabilmeniz için Çözümünüzün birden fazla projeden oluşması gerekir.

### <a name="to-remove-dependencies-from-projects"></a>Projelerden bağımlılıkları kaldırmak için

1. Çözüm Gezgini bir proje seçin.

2. **Proje** menüsünde **Proje bağımlılıkları**' nı seçin.

     **Proje bağımlılıkları** iletişim kutusu açılır.

    > [!NOTE]
    > **Proje bağımlılıkları** seçeneği yalnızca birden fazla proje içeren bir çözümde kullanılabilir.

3. **Bağımlılıklar** sekmesinde, **Proje** açılan menüsünden bir proje seçin.

4. **Bağlı** alanında, bu projenin artık bağımlılıkları olmayan diğer projelerin yanındaki onay kutularını temizleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'Da projeler ve çözümler oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [](../ide/compiling-and-building-in-visual-studio.md) [derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md) [nib nasıl yapılır: proje özelliklerini ve yapılandırma ayarlarını değiştirme](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
