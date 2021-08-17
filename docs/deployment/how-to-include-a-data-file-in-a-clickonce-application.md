---
title: ClickOnce uygulamasına veri dosyası dahil edin
description: Hedef bilgisayar yerel disk üzerinde bir veri dizininde depo ClickOnce herhangi bir türde veri dosyasını uygulamanıza nasıl ekleyebilirsiniz?
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 225c24e4bb743b26a137b68e206a5937963f6e28
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080604"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Nasıl kullanılır: Bir veri dosyasını ClickOnce dahil
Yükley istediğiniz her uygulamaya hedef bilgisayarın yerel disk üzerinde uygulamanın kendi verilerini [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yönetecekleri bir veri dizini atanır. Veri dosyaları herhangi bir türde dosya içerebilir: metin dosyaları, XML dosyaları, hatta Microsoft Access veritabanı (*.mdb*) dosyaları. Aşağıdaki yordamlar, uygulamanıza herhangi bir türde veri dosyası eklemeyi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gösterir.

### <a name="to-include-a-data-file-by-using-mageexe"></a>Veri dosyası eklemek için Mage.exe

1. Veri dosyasını, uygulamanın diğer dosyalarıyla birlikte uygulama dizininize ekleyin.

    Genellikle uygulama dizininiz, dağıtımın geçerli sürümüyle etiketlenmiş bir dizin (örneğin, v1.0.0.0) olur.

2. Uygulama bildiriminizi güncelleştirin ve veri dosyasını listelenin.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    Bu görevi gerçekleştirerek uygulama bildiriminizin dosya listesini yeniden oluşturur ve ayrıca karma imzaları otomatik olarak oluşturur.

3. Uygulama bildirimini tercih ettiğiniz metinde veya XML düzenleyicisinde açın ve son `file` eklenen dosyanız için öğesini bulun.

    adlı bir XML dosyası `Data.xml` eklediysanız, dosya aşağıdaki kod örneğine benzer şekilde olur.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. özniteliğini `type` bu öğeye ekleyin ve değeriyle birlikte `data` ekleyin.

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Anahtar çiftini veya sertifikanızı kullanarak uygulama bildiriminizi yeniden imzalar ve ardından dağıtım bildiriminizi yeniden imzalar.

    Uygulama bildiriminin karması değiştirilen dağıtım bildiriminizi yeniden imzalamanız gerekir.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Veri dosyası eklemek için MageUI.exe

1. Veri dosyasını, uygulamanın diğer dosyalarıyla birlikte uygulama dizininize ekleyin.

2. Genellikle uygulama dizininiz, dağıtımın geçerli sürümüyle etiketlenmiş bir dizin (örneğin, v1.0.0.0) olur.

3. Dosya menüsünde **Aç'a** **tıklar** ve uygulama bildiriminizi açın.

4. Dosyalar **sekmesini** seçin.

5. Sekmenin üst kısmında yer alan metin kutusuna, uygulama dosyalarınızı içeren dizini girin ve ardından **Doldurmak'a tıklayın.**

     Veri dosyanız kılavuzda görünür.

6. Veri **dosyasının Dosya** Türü değerini Veri olarak **ayarlayın.**

7. Uygulama bildirimini kaydedin ve ardından dosyayı yeniden imzalar.

     *MageUI.exe* yeniden imzalamanız istenir.

8. Dağıtım bildiriminizi yeniden imzalama

     Uygulama bildiriminin karması değiştirilen dağıtım bildiriminizi yeniden imzalamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarında yerel ve uzak veri erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)