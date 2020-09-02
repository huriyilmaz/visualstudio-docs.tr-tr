---
title: 'Nasıl yapılır: Görselleştirici kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
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
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778368"
---
# <a name="how-to-use-a-visualizer"></a>Nasıl Yapılır: Görselleştirici Kullanma
Bir değişken ya da nesnenin içeriğini veri türü için anlamlı bir biçimde göstermek için Görselleştirici kullanabilirsiniz. Görsel öğeleri **DataTips**, bir **Gözcü** penceresi, **oto** penceresi veya **Locals** penceresinden kullanabilirsiniz.  
  
 Görselleyiciler Compact Framework 'te desteklenmez.  
  
> [!NOTE]
> **Mağaza** uygulamalarında yalnızca standart metın, HTML, XML ve JSON Görselleştiriciler desteklenir. Özel (Kullanıcı tarafından oluşturulan) Görselleştiriciler desteklenmez.  
  
### <a name="to-open-a-visualizer"></a>Görselleştirici açmak için  
  
1. **DataTips**, bir **Gözcü** penceresinde veya **oto**, **Yereller**veya **hızlı gözcü** penceresinde bir değişken adının yanında görünen büyüteç simgesine tıklayın.  
  
     Görselleştiricilerin bir listesi görüntülenir.  
  
2. Kullanmak istediğiniz Görselleştirici tıklayın.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Uzaktan hata ayıklama sırasında yönetilen kod için Görselleştirici kullanmak için  
  
- Hata ayıklama oturumuna başlamadan önce Görselleştirici DLL 'ini uzak bilgisayara kopyalayın.  
  
     DLL yolu hem uzak hem de yerel bilgisayarlarda aynı olmalıdır. Bu yol aşağıdaki konumlardan herhangi biri olabilir:  
  
     *Visual Studio yüklemesi yolu*`\Common7\Packages\Debugger\Visualizers`  
  
     -veya-  
  
     `My Documents\Visual Studio 2010\Visualizers`*Visual Studio sürümü*`\Visualizers`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [Nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md)   
 [Nasıl yapılır: Görselleştirici Yazma](../debugger/how-to-write-a-visualizer.md)   
 [Veri İpuçları'ndaki veri değerlerini görüntüleme](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)