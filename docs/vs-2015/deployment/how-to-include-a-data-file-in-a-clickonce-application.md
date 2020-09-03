---
title: 'Nasıl yapılır: ClickOnce uygulamasına veri dosyası ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9120a5b3cb60f6c607ed97ab2df24bb157c72371
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153777"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Nasıl yapılır: ClickOnce Uygulamasına bir Veri Dosyası Dahil Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Yüklediğiniz her uygulamaya, uygulamanın kendi verilerini yönetebileceği hedef bilgisayarın yerel diskinde bir veri dizini atanır. Veri dosyaları herhangi bir türde dosya içerebilir: metin dosyaları, XML dosyaları, hatta Microsoft Access veritabanı (. mdb) dosyaları. Aşağıdaki yordamlarda, uygulamanıza herhangi bir türde veri dosyasını nasıl ekleyeceğiniz gösterilmektedir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Mage.exe kullanarak bir veri dosyası eklemek için  
  
1. Veri dosyasını uygulamanızın geri kalanı ile uygulama dizininize ekleyin.  
  
    Genellikle, uygulama dizininiz dağıtımın geçerli sürümüyle etiketlenmiş bir dizin olacaktır — örneğin, v 1.0.0.0.  
  
2. Veri dosyasını listelemek için uygulama bildiriminizi güncelleştirin.  
  
    **mage-u v 1.0.0.0 \ Application. manifest-FromDirectory v 1.0.0.0**  
  
    Bu görevi gerçekleştirmek, uygulama bildiriminizde dosyaların listesini yeniden oluşturur ve ayrıca karma imzaları otomatik olarak oluşturur.  
  
3. Uygulama bildirimini tercih ettiğiniz metin veya XML düzenleyicisinde açın ve `file` son eklenen dosyanız için öğesini bulun.  
  
    Adlı bir XML dosyası eklediyseniz `Data.xml` , dosya aşağıdaki kod örneğine benzer şekilde görünür.  
  
   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
4. Özniteliğini `type` Bu öğeye ekleyin ve değerini sağlayın `data` .  
  
   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
5. Anahtar çiftinizi veya sertifikanızı kullanarak uygulama bildiriminizi yeniden imzalayın ve ardından Dağıtım bildiriminizi yeniden imzalayın.  
  
    Uygulama bildiriminin karması değiştiğinden Dağıtım bildiriminizi yeniden imzalamanız gerekir.  
  
    **mage-s uygulama bildirimi-CF cert_file-PWD parolası**  
  
    **mage-u dağıtım bildirimi-APPM uygulama bildirimi**  
  
    **mage-s dağıtım bildirimi-CF SertifikaDosyası-PWD parolası**  
  
6. 
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>MageUI.exe kullanarak bir veri dosyası eklemek için  
  
1. Veri dosyasını uygulamanızın geri kalanı ile uygulama dizininize ekleyin.  
  
2. Genellikle, uygulama dizininiz dağıtımın geçerli sürümüyle etiketlenmiş bir dizin olacaktır — örneğin, v 1.0.0.0.  
  
3. **Dosya** menüsünde, uygulama bildiriminizi açmak için **Aç** ' a tıklayın.  
  
4. **Dosyalar** sekmesini seçin.  
  
5. Sekmenin en üstündeki metin kutusuna uygulamanızın dosyalarını içeren dizini girin ve ardından **doldur**' a tıklayın.  
  
     Veri dosyanız kılavuzda görüntülenir.  
  
6. Veri dosyasının **dosya türü** değerini **veri**olarak ayarlayın.  
  
7. Uygulama bildirimini kaydedin ve sonra dosyayı yeniden imzalayın.  
  
     MageUI.exe, dosyayı yeniden imzalamanız istenir.  
  
8. Dağıtım bildiriminizi yeniden imzalama  
  
     Uygulama bildiriminin karması değiştiğinden Dağıtım bildiriminizi yeniden imzalamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Uygulamalarında Yerel ve Uzak Veri Erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
