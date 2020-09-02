---
title: "Nasıl yapılır: Düzenle ve devam et 'i kullanma (C#) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807200"
---
# <a name="how-to-use-edit-and-continue-c"></a>Nasıl Yapılır: Düzenle ve Devam Et'i Kullanma (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C# için Düzenle ve devam et ile, hata ayıklama sırasında kodunuzda kesme modunda değişiklikler yapabilirsiniz. Değişiklikler hata ayıklama oturumunu durdurup yeniden başlatmaya gerek kalmadan uygulanabilir.  
  
 Düzenle ve devam et, kesme modunda değişiklikler yaptığınızda otomatik olarak çağrılır, ardından **devam et**, **adımla**veya **sonraki ifadeyi ayarla**gibi bir hata ayıklayıcı yürütme komutu seçin ya da bir hata ayıklayıcı penceresindeki bir işlevi değerlendirin.  
  
> [!NOTE]
> Düzenleme ve devam etme, sıkıştırma çerçevesi, iyileştirilmiş kod, karma yerel/yönetilen kod veya SQL Server ortak dil çalışma zamanı (CLR) tümleştirme kodu hata ayıklaması sırasında desteklenmez. Bu senaryolardan birinde kod değişiklikleri uygulamaya çalışırsanız, hata ayıklayıcı Düzenle ve devam et ' in desteklenmediğini belirten bir iletişim kutusu koyar.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Düzenle 'yi çağırmak ve otomatik olarak devam etmek için  
  
1. Kesme modunda, kaynak kodunuzda bir değişiklik yapın.  
  
2. **Hata ayıklama** menüsünde, **devam et**, **adımla**veya **sonraki ifadeyi ayarla** ya da bir hata ayıklayıcı penceresindeki bir işlevi değerlendir ' e tıklayın.  
  
     Yeni kod derlenir ve hata ayıklama yeni kodla devam eder. Bazı değişiklikler Düzenle ve devam et tarafından desteklenmiyor. Daha fazla bilgi için bkz. [desteklenen kod değişiklikleri (C#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Düzenle ve devam et 'i etkinleştirmek/devre dışı bırakmak için  
  
1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.  
  
2. **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümünü genişletin ve **Düzenle ve devam et**' i seçin.  
  
3. **Seçenekler** Iletişim kutusu **Düzenle ve devam et** sayfasında **Düzenle ve devam et 'i etkinleştir** onay kutusunu işaretleyin veya temizleyin.  
  
     Ayar, hata ayıklama oturumunu yeniden başlattığınızda devreye girer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenle ve devam et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Desteklenen kod değişiklikleri (C#)](../debugger/supported-code-changes-csharp.md)   
 [Düzenle ve Devam Et Hataları ve Uyarıları (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
