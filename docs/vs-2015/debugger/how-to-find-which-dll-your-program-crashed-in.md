---
title: "Nasıl yapılır: programınızın hangi DLL 'de kilitlendiğini bulma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 44ebe042ff6e2507530e4be410e768550e922b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703625"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Nasıl Yapılır: Programınızın Hangi DLL'de Kilitlendiğini Bulma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTUN
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Uygulamanız bir sistem DLL 'SI veya başka birinin kodu çağrısı sırasında kilitlenirse, kilitlenme oluştuğunda hangi DLL 'nin etkin olduğunu bulmanız gerekir. Kendi programınızın dışında bir DLL 'de kilitlenmeyle karşılaşırsanız, bu konumu **modüller** penceresini kullanarak belirleyebilirsiniz.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Modüller penceresini kullanarak bir kilitlenmenin nerede oluştuğunu bulmak için  
  
1. Çökmenin gerçekleştiği adresi aklınızda edin.  
  
2. **Hata Ayıkla** menüsünde **Windows**' u seçin ve **modüller**' e tıklayın.  
  
3. **Modüller** penceresinde **Adres** sütununu bulun. Bunu görmek için kaydırma çubuğunu kullanmanız gerekebilir.  
  
4. Dll 'Leri adrese göre sıralamak için sütunun en üstündeki **Adres** düğmesine tıklayın.  
  
5. Adres aralığı kilitlenme konumunu içeren DLL 'yi bulmak için sıralanmış listeyi tarayın.  
  
6. DLL adını ve yolunu görmek için **ad** ve **yol** sütunlarına bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yerel dll 'Lerde hata ayıklama](../debugger/how-to-debug-native-dlls.md)   
 [Nasıl Yapılır: Modüller Penceresini Kullanma](../debugger/how-to-use-the-modules-window.md)
