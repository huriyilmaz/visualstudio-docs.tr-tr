---
title: WCF hata ayıklama sınırlamaları | Microsoft Docs
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
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3faa57a0a2ca413898364c2d4ad1891df85f1ce8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176808"
---
# <a name="limitations-on-wcf-debugging"></a>WCE Hata Ayıklamasında Sınırlamalar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WCF hizmetinde hata ayıklamaya başlayabilmeniz için kullanabileceğiniz üç yol vardır:  
  
- Hizmet çağıran bir istemci işleminde hata ayıklaması yapıyorsanız. Hizmetin hata ayıklayıcı adımları. Hizmetin, istemci uygulamanızla aynı çözümde olması gerekmez.  
  
- Bir hizmete istek yapan bir istemci işlemini hata ayıklaması yapıyorsanız. Hizmet çözümünüzün bir parçası olmalıdır.  
  
- Şu anda çalışmakta olan bir hizmete iliştirmek için **Ekle işlemini** kullanırsınız. Hata ayıklama, hizmet içinde başlar.  
  
  Bu konuda bu senaryolara ilişkin sınırlamalar açıklanmaktadır.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Bir hizmeti adımla ilgili sınırlamalar  
 Hata ayıkladığınız istemci uygulamalarından bir hizmete geçmek için aşağıdaki koşulların karşılanması gerekir:  
  
- İstemci, zaman uyumlu bir istemci nesnesi kullanarak hizmeti çağırmalıdır.  
  
- Sözleşme işlemi tek yönlü olamaz.  
  
- Sunucu zaman uyumsuz ise, hizmet içinde kod yürütürken tam çağrı yığınını görüntüleyemezsiniz.  
  
- app.config veya Web.config dosyasında aşağıdaki kodla hata ayıklamanın etkinleştirilmesi gerekir:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Bu kod yalnızca bir kez eklenmelidir. Bu kodu,. config dosyasını düzenleyerek veya **Işleme İliştir**' i kullanarak hizmete ekleyerek ekleyebilirsiniz. Bir hizmette **Işleme ekleme** kullandığınızda, hata ayıklama kodu otomatik olarak. config dosyasına eklenir. Bundan sonra,. config dosyasını düzenlemek zorunda kalmadan hata ayıklamanıza ve hizmette ilerme yapabilirsiniz.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Bir hizmetten atlama sınırlamaları  
 Bir hizmetin ve istemciye geri dönme işlemi, bir hizmetin adımlaması için açıklanan sınırlamalara sahiptir. Buna ek olarak, hata ayıklayıcı istemciye eklenmelidir. Bir istemcide hata ayıklaması yapıyorsanız ve bir hizmete adımla, hata ayıklayıcı hizmete bağlı kalır. Bu, istemciyi, **hata ayıklamayı Başlat** ' i kullanarak veya istemciye Iliştirerek, **İşleme İliştir**' i kullanarak başlatmış olmanız durumunda geçerlidir. Hizmete ekleyerek hata ayıklamaya başladıysanız, hata ayıklayıcı henüz istemciye eklenmez. Bu durumda, hizmeti kullanıma almak ve istemciye geri dönmek istiyorsanız, öncelikle istemciye el ile eklemek için **Ekle işlemini** kullanmanız gerekir.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Bir hizmete otomatik Iliştirme sınırlamaları  
 Bir hizmete otomatik iliştirme aşağıdaki sınırlamalara sahiptir:  
  
- Hizmet, hata ayıkladığınız çözümün bir parçası olmalıdır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Hizmet barındırılıyor olmalıdır. Bir Web sitesi projesinin (dosya sistemi ve HTTP), Web uygulaması projesinin (dosya sistemi ve HTTP) veya WCF hizmet kitaplığı projesinin bir parçası olabilir. WCF hizmet kitaplığı projeleri hizmet kitaplıkları veya Iş akışı hizmeti kitaplıkları olabilir.  
  
- Hizmetin bir WCF istemcisinden çağrılması gerekir.  
  
- app.config veya Web.config dosyasında aşağıdaki kodla hata ayıklamanın etkinleştirilmesi gerekir:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>Kendi kendine barındırma  
 *Şirket içinde barındırılan bir hizmet* , IIS 'de, WCF hizmeti ana bilgisayarında veya geliştirme sunucusunda ÇALıŞTıRMAYAN bir WCF hizmetidir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Şirket içinde barındırılan bir hizmette hata ayıklama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Şirket Içinde BARıNDıRıLAN WCF hizmetinde hata ayıklama](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Kendi kendine barındırma  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]3,0 veya 3,5 uygulamalarında hata ayıklamayı etkinleştirmek için, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] önce 3,0 veya 3,5 yüklü olmalıdır [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] . [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3,0 veya 3,5 ' den önce yüklendiyse, bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3,0 veya 3,5 uygulamasında hata ayıklamaya çalıştığınızda bir hata oluşur. "Sunucuda otomatik olarak adımla" hata iletisi görüntülenir. Bu sorunu gidermek için Windows **Denetim Masası**, **Programlar ve Özellikler** ' i kullanarak [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] yüklemenizi onarın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF hizmetlerinde hata ayıklama](../debugger/debugging-wcf-services.md)   
 [Nasıl Yapılır: Kendini Barındıran WCF Hizmetinde Hata Ayıklama](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
