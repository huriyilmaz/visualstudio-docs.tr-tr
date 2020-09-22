---
title: ClickOnce uygulamasına bir veri dosyası dahil etme
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cdc2154876724feb5c6a0329a2acc5df7ac80fbc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809152"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil etme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Yüklediğiniz her uygulamaya, uygulamanın kendi verilerini yönetebileceği hedef bilgisayarın yerel diskinde bir veri dizini atanır. Veri dosyaları herhangi bir türde dosya içerebilir: metin dosyaları, XML dosyaları, hatta Microsoft Access veritabanı (*. mdb*) dosyaları. Aşağıdaki yordamlarda, uygulamanıza herhangi bir türde veri dosyasını nasıl ekleyeceğiniz gösterilmektedir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

### <a name="to-include-a-data-file-by-using-mageexe"></a>Mage.exe kullanarak bir veri dosyası eklemek için

1. Veri dosyasını uygulamanızın geri kalanı ile uygulama dizininize ekleyin.

    Genellikle, uygulama dizininiz dağıtımın geçerli sürümüyle etiketlenmiş bir dizin olacaktır — örneğin, v 1.0.0.0.

2. Veri dosyasını listelemek için uygulama bildiriminizi güncelleştirin.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    Bu görevi gerçekleştirmek, uygulama bildiriminizde dosyaların listesini yeniden oluşturur ve ayrıca karma imzaları otomatik olarak oluşturur.

3. Uygulama bildirimini tercih ettiğiniz metin veya XML düzenleyicisinde açın ve `file` son eklenen dosyanız için öğesini bulun.

    Adlı bir XML dosyası eklediyseniz `Data.xml` , dosya aşağıdaki kod örneğine benzer şekilde görünür.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. Özniteliğini `type` Bu öğeye ekleyin ve değerini sağlayın `data` .

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Anahtar çiftinizi veya sertifikanızı kullanarak uygulama bildiriminizi yeniden imzalayın ve ardından Dağıtım bildiriminizi yeniden imzalayın.

    Uygulama bildiriminin karması değiştiğinden Dağıtım bildiriminizi yeniden imzalamanız gerekir.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>MageUI.exe kullanarak bir veri dosyası eklemek için

1. Veri dosyasını uygulamanızın geri kalanı ile uygulama dizininize ekleyin.

2. Genellikle, uygulama dizininiz dağıtımın geçerli sürümüyle etiketlenmiş bir dizin olacaktır — örneğin, v 1.0.0.0.

3. **Dosya** menüsünde, uygulama bildiriminizi açmak için **Aç** ' a tıklayın.

4. **Dosyalar** sekmesini seçin.

5. Sekmenin en üstündeki metin kutusuna uygulamanızın dosyalarını içeren dizini girin ve ardından **doldur**' a tıklayın.

     Veri dosyanız kılavuzda görüntülenir.

6. Veri dosyasının **dosya türü** değerini **veri**olarak ayarlayın.

7. Uygulama bildirimini kaydedin ve sonra dosyayı yeniden imzalayın.

     *MageUI.exe* , dosyayı yeniden imzalamanız istenir.

8. Dağıtım bildiriminizi yeniden imzalama

     Uygulama bildiriminin karması değiştiğinden Dağıtım bildiriminizi yeniden imzalamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarında yerel ve uzak veri erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)