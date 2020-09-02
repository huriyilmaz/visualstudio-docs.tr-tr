---
title: 'Nasıl yapılır: hata ayıklama Için bir .NET Framework sürümü belirtme | Microsoft Docs'
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
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4c785c419ead31ad90e2b20ae7f48af778598bb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176565"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Nasıl Yapılır: Hata Ayıklama İçin .NET Framework Sürümü Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]Hata ayıklayıcı, Microsoft 'un eski sürümlerinin [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] yanı sıra geçerli sürümü de hata ayıklamayı destekler. Visual Studio 'dan bir uygulama başlatırsanız hata ayıklayıcı, hata ayıklaması yaptığınız uygulamanın doğru sürümünü her zaman tanımlayabilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Uygulama zaten çalışıyorsa ve **Ekle**' yi kullanırsanız, hata ayıklayıcı her zaman eski bir sürümünü tanımlayamayabilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Bu durumda, şöyle bir hata iletisi alırsınız.  
  
 Hata ayıklayıcı uygulamanızın kullanacağı sürüm hakkında yanlış bir varsayım yaptı [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Nadir durumlarda, hangi sürümü kullanacağınızı hata ayıklayıcıya göstermek için bir kayıt defteri anahtarı ayarlayabilirsiniz.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Hata ayıklama için bir .NET Framework sürümünü belirtmek için  
  
1. Makinenizde yüklü .NET Framework sürümlerini bulmak için Windows\Microsoft.NET\Framework dizinine bakın. Sürüm numaraları şuna benzer:  
  
     `V1.1.4322`  
  
     Doğru sürüm numarasını belirleyip bunu bir yere göz önünde yapın.  
  
2. **Kayıt defteri Düzenleyicisi 'ni** (regedit) başlatın.  
  
3. **Kayıt defteri düzenleyicisinde**HKEY_LOCAL_MACHINE klasörünü açın.  
  
4. Şuraya gidin: HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine \\ {449Ec4cc-30D2-4032-9256-EE18EB41B62B}  
  
     Anahtar yoksa, HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine ' e sağ tıklayın ve **Yeni anahtar**' a tıklayın. Yeni anahtarı adlandırın `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` .  
  
5. {449EC4CC-30D2-4032-9256-EE18EB41B62B} sayfasına gittikten sonra **ad** sütununa bakın ve CLRVersionForDebugging anahtarını bulun.  
  
    1. Anahtar yoksa, {449EC4CC-30D2-4032-9256-EE18EB41B62B} öğesine sağ tıklayın ve **Yeni dize değeri**' ne tıklayın. Ardından yeni dize değerine sağ tıklayın, **Yeniden Adlandır**' a tıklayın ve yazın `CLRVersionForDebugging` .  
  
6. **CLRVersionForDebugging**öğesine çift tıklayın.  
  
7. **Dize Düzenle** kutusuna **değer** kutusuna .NET Framework sürüm numarasını yazın. Örneğin: V 1.1.4322  
  
8. **Tamam**’a tıklayın.  
  
9. **Kayıt defteri düzenleyicisini**kapatın.  
  
     Hata ayıklamaya başladığınızda yine de bir hata iletisi alırsanız, sürüm numarasını kayıt defterine doğru girdiğinizden emin olun. Ayrıca, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Visual Studio tarafından desteklenen bir sürümünü kullandığınızı doğrulayın. Hata ayıklayıcı geçerli .NET Framework sürümü ve önceki sürümlerle uyumludur, ancak gelecekteki sürümlerle uyumlu olmayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)
