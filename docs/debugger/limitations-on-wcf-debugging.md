---
title: WCF Hata Ayıklama | Microsoft Docs
description: WCF hizmetinde hata ayıklamaya başlamanın yollarını, gerekli koşulları ve hata ayıklama sınırlamalarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ee9709d77d5e359d14cbfa30ae23e3bfc9e94a68
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080747"
---
# <a name="limitations-on-wcf-debugging"></a>WCE Hata Ayıklamasında Sınırlamalar
WCF hizmetinde hata ayıklamaya başlamak için üç yol vardır:

- Bir hizmeti çağıran bir istemci işlemi için hata ayıklayabilirsiniz. Hata ayıklayıcısı hizmete adım adım ilerler. Hizmetin istemci uygulamayla aynı çözümde olması gerek değildir.

- Bir hizmete istekte bulunduran bir istemci işleminin hatasını ayıklayabilirsiniz. Hizmetin çözüme bir parçası olması gerekir.

- Şu anda **çalışan bir hizmete** iliştirmek için İşleme Ekle'leri kullanırsiniz. Hata ayıklama hizmetin içinde başlar.

Bu konu başlığında bu senaryolarla ilgili sınırlamalar açıklanmıştır.

## <a name="limitations-on-stepping-into-a-service"></a>Hizmete Adımlama Sınırlamaları
 Hata ayıklamakta olduğunu istemci uygulamalarından bir hizmete adımlamanız için aşağıdaki koşulların karşı olması gerekir:

- İstemcinin zaman uyumlu bir istemci nesnesi kullanarak hizmeti çağırması gerekir.

- Anlaşma işlemi tek yol olamaz.

- Sunucu zaman uyumsuzsa, hizmetin içinde kod yürütürken tam çağrı yığınını görüntüamazsınız.

- Hata ayıklama, app.config veya Web.config etkinleştirilmelidir:

    ```xml
    <system.web>
      <compilation debug="true" />
    </system.web>
    ```

     Bu kodun yalnızca bir kez eklenmiş olması gerekir. Bu kodu eklemek için dosyanın .config veya İşleme Ekle'yi kullanarak **hizmete iliştirebilirsiniz.** Bir **hizmette İşleme** Ekle'leri kullanırsanız, hata ayıklama kodu otomatik olarak .config eklenir. Bundan sonra, hata ayıklar ve dosyanın hata ayıklama dosyasını düzenlemek zorunda kalmadan .config adım atabilirsiniz.

## <a name="limitations-on-stepping-out-of-a-service"></a>Bir Hizmette Dışarı Adımlama Sınırlamaları
 Bir hizmette adımlama ve istemciye geri dönme, hizmete adımlamayla ilgili sınırlamalarla aynıdır. Ayrıca, hata ayıklayıcısı istemciye ekli olması gerekir. Bir istemcide hata ayıklar ve bir hizmete adımlarsanız, hata ayıklayıcı hizmete bağlı kalır. Hata Ayıklamayı Başlat'ı kullanarak istemciyi **başlatsanız** veya İşleme İliştir'i kullanarak istemciye eklenmiş **de olsa bu durum doğrudur.** Hata ayıklamaya hizmete iliştirerek başladıysanız, hata ayıklayıcı henüz istemciye bağlı değildir. Bu durumda, hizmet dışında bir adım atarak istemciye geri dönmeniz  gerekirse, istemciye el ile eklemek için önce İşleme Ekle'ye ekle'sini kullanmalısınız.

## <a name="limitations-on-automatic-attach-to-a-service"></a>Hizmete Otomatik Ekleme Sınırlamaları
 Bir hizmete otomatik olarak eklemenin aşağıdaki sınırlamaları vardır:

- Hizmet, hata ayıklamakta [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olduğunuz çözümün parçası olması gerekir.

- Hizmetin barındırnmış olması gerekir. Bir Web Sitesi projesinin (Dosya Sistemi ve HTTP), Web Uygulaması projesinin (Dosya Sistemi ve HTTP) veya WCF Hizmet Kitaplığı projesinin parçası olabilir. WCF Hizmet Kitaplığı projeleri Hizmet Kitaplıkları veya İş Akışı Hizmet Kitaplıkları olabilir.

- Hizmetin bir WCF istemciden çağrılsı gerekir.

- Hata ayıklama, app.config veya Web.config etkinleştirilmelidir:

  ```xml
  <system.web>
    <compilation debug="true" />
  <system.web>
  ```

## <a name="self-hosting"></a>Self-Hosting
 Kendinden *konak hizmet IIS,* WCF Hizmet Ana Bilgisayarı veya Geliştirme Sunucusu içinde çalıştır olmayan bir WCF [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hizmetidir. Kendinden konak hizmette hata ayıklama hakkında daha fazla bilgi için bkz. Nasıl 2014'Self-Hosted [WCF Hizmeti'nin hata ayıklaması.](../debugger/how-to-debug-a-self-hosted-wcf-service.md)

 3.0 veya 3.5 uygulamalarında hata ayıklamayı etkinleştirmek için, yüklenmeden önce [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 veya 3.5'in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] yüklü olması gerekir. [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 veya 3.5'den önce yüklendiyse, 3.0 veya 3.5 uygulamasında hata ayıklamayı denemiş [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] olursanız bir hata oluşur. Hata iletisi şudur: "Sunucuya Otomatik Olarak Adımlama Başarısız." Bu sorunu çözmek için, yüklemenizi onarmak Windows **Denetim Masası**  >  **Programlar ve Özellikler'i** [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [WCF Hizmetlerinde Hata Ayıklama](../debugger/debugging-wcf-services.md)
- [Nasıl Yapılır: Kendini Barındıran WCF Hizmetinde Hata Ayıklama](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
