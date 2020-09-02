---
title: 'Nasıl yapılır: Görselleştirici yüklemesi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726cea8b2e81c53b5f3fff963357946f26b199f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796965"
---
# <a name="how-to-install-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştirici oluşturduktan sonra, ' de kullanılabilir olacak şekilde Görselleştirici 'yı yüklemelisiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Görselleştirici yüklenmesi basit bir işlemdir.  
  
> [!NOTE]
> **Mağaza** uygulamalarında yalnızca standart metın, HTML, XML ve JSON Görselleştiriciler desteklenir. Özel (Kullanıcı tarafından oluşturulan) Görselleştiriciler desteklenmez.  
  
### <a name="to-install-a-visualizer"></a>Görselleştirici yüklemek için  
  
1. Derleyecek Görselleştiriciyi içeren DLL 'i bulun.  
  
2. DLL 'yi aşağıdaki konumlardan birine kopyalayın:  
  
    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    - `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3. Uzaktan hata ayıklama için yönetilen bir Görselleştirici kullanmak istiyorsanız, uzak bilgisayardaki aynı yola DLL 'yi kopyalayın.  
  
4. Hata ayıklama oturumunu yeniden başlatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [Nasıl Yapılır: Görselleştirici Yazma](../debugger/how-to-write-a-visualizer.md)
