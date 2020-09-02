---
title: 'Nasıl yapılır: karma modda hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5e2dd4ea0000eefdbd9f74c8fa97c4c63e06fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681143"
---
# <a name="how-to-debug-in-mixed-mode"></a>Nasıl Yapılır: Karışık Modda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki yordamlar, hem yönetilen hem de yerel kodda, karışık modda hata ayıklama olarak da bilinen hata ayıklamanın nasıl yapılacağını açıklamaktadır. DLL veya uygulamanın yerel kodda yazılı olmasına bağlı olarak, bunu yapmanın iki senaryosu vardır:  
  
- DLL 'nizi çağıran çağıran uygulama yerel kodda yazılır. Bu durumda, DLL 'niz yönetilir ve hem yönetilen hem de yerel hata ayıklayıcıların her ikisinde de hata ayıklaması için etkinleştirilmesi gerekir. Bunu ** \<Project> Özellik sayfaları** iletişim kutusunda kontrol edebilirsiniz. Bunu yaptığınızda, DLL projesinden veya çağıran uygulama projesinden hata ayıklamayı başlatıp başlatdığınıza bağlıdır.  
  
- DLL 'nizi çağıran çağıran uygulama yönetilen kodda yazılır ve DLL 'niz yerel kodda yazılır.  
  
> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Karışık modda hata ayıklamayı etkinleştirmek için  
  
1. **Çözüm Gezgini**, projeyi seçin.  
  
2. **Görünüm** menüsünde, **Özellik sayfaları**' na tıklayın.  
  
3. ** \<Project> Özellik sayfaları** Iletişim kutusunda, **yapılandırma özellikleri** düğümünü genişletin ve ardından **hata ayıklama**öğesini seçin.  
  
4. **Hata ayıklayıcı türünü** **karışık** veya **Otomatik**olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: DLL projesinde hata ayıklama](../debugger/how-to-debug-from-a-dll-project.md)
