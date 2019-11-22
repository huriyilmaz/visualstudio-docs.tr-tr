---
title: VSıX paketleri imzalanıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b74222804e9ed42e6f8263cbe6ad0daf19cda81f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300330"
---
# <a name="signing-vsix-packages"></a>VSIX Paketlerini İmzalama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzantı derlemelerinin Visual Studio 'da çalıştırılmadan önce imzalanması gerekmez, ancak bunu yapmak iyi bir uygulamadır.  
  
 Uzantınızı güvenli hale getirmek ve kurcalanmadığından emin olmak istiyorsanız VSıX paketine dijital imza ekleyebilirsiniz. Bir VSıX imzalandığı zaman VSıX yükleyicisi, imzalandığını belirten bir ileti ve imzanın kendisi hakkında daha fazla bilgi görüntüler. VSıX içeriği değiştirilmişse ve VSıX yeniden imzalanmamışsa, VSıX yükleyicisi imza geçerli değil olarak gösterilir. Yükleme durdurulmaz, ancak Kullanıcı uyarıladır.  
  
> [!IMPORTANT]
> 2015 ' den başlayarak, SHA256 şifrelemesi dışında bir şey kullanılarak imzalanmış VSıX paketleri geçersiz imzaya sahip olacak şekilde tanımlanır. VSıX yüklemesi engellenmiyor, ancak Kullanıcı uyarılacaktır.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Valtsigntool ile VSıX imzalama  
 [Valtsigntool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)'de NuGet.org üzerinde [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) tarafından kullanılabilen bir SHA256 şifreleme imzalama aracı vardır.  
  
#### <a name="to-use-the-vsixsigntool"></a>Valtsigntool kullanmak için  
  
1. VSıX 'i bir projeye ekleyin.  
  
2. Çözüm Gezgini ' de proje düğümüne sağ tıklayıp **NuGet Paketlerini Yönet Ekle &#124;** ' yi seçin.  NuGet ve NuGet paketleri ekleme hakkında daha fazla bilgi için bkz. [NuGet 'e genel bakış](https://docs.microsoft.com/nuget/) ve [Iletişim kutusunu kullanarak NuGet paketlerini yönetme](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio).  
  
3. VisualStudioExtensibility adresinden Valtsigntool araması yapın ve NuGet paketini yükledikten sonra.  
  
4. Şimdi de, projenin yerel paketler konumundan Valtsigntool öğesini çalıştırabilirsiniz. İmzalama senaryonuz (Valtsigntool. exe/?) için araç komut satırı yardımına bakın.  
  
   Örneğin, parola korumalı bir sertifika dosyası ile imzalamak için:  
  
   Valtsigntool. exe Sign/f \<SertifikaDosyası >/p \<parola > \<Valtfile >  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)
