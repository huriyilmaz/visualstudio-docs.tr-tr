---
title: Eski dil hizmeti geliştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 36ff8335bfaf99b5826d217a48910bfd581321e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805196"
---
# <a name="developing-a-legacy-language-service"></a>Eski Dil Hizmeti Geliştirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu bölüm, eski dil hizmeti oluşturmanıza yardımcı olan konulara bağlantı sağlar.  
  
 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Dil hizmeti uygulama hakkında daha fazla bilgi edinmek için bkz. [Düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Eski Dil Hizmetinin Modeli](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Çekirdek Düzenleyici için en düşük dil hizmetinin bir modelini sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Bu modeli, kendi dil hizmetinizi oluşturmak için bir kılavuz olarak kullanabilirsiniz.  
  
 [Eski Dil Hizmeti Arabirimleri](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Bir dil hizmetini uygulamak için gereken nesneleri açıklar ve söz dizimi vurgulaması, yöntem verileri ve diğer özellikleri sağlamak için kullanabileceğiniz ek nesnelerin bir listesini sağlar.  
  
 [Eski Dil Hizmeti Komutlarını Kesme](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Metin görünümünün daha sonra işleyeceği komutları ele almak için dil hizmetinize bir komut filtresi eklemeyi açıklar.  
  
 [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Kullanarak dil hizmetinizi kaydetme hakkında bilgi sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Hata Ayıklama için Dil Hizmeti Desteği](../../extensibility/internals/language-service-support-for-debugging.md)  
 Bir dil hizmetinin bir hata ayıklayıcıyı desteklemek için nasıl özellik sağlayabileceğinizi açıklar.  
  
 [Yapılacaklar listesi: Eski Dil Hizmeti oluşturma](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Çekirdek Düzenleyici için dil hizmeti oluşturmak ve tümleştirmek için adım adım yönergeler sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Dil hizmetinize nasıl sözdizimi vurgulamanın uygulanacağını açıklar.  
  
 [Eski Dil Hizmetinde Deyim Tamamlama](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Bir dil hizmetinin, kullanıcıların yazmaya başladıkları bir dil anahtar sözcüğünü veya öğesini bitirmesini yardım eden işlem olan deyimin tamamlanmasını açıklar.  
  
 [Eski Dil Hizmetinde Parametre Bilgileri](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Aşırı yüklenmiş işlevler ve yöntemler için nasıl Yöntem ipuçları sağlayabileceğinizi açıklar.  
  
 [Nasıl yapılır: Eski Dil Hizmetinde Gizli Metin Desteği Sağlama](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Gizli bir metin bölgesinin amacını açıklar ve gizli metin bölgesinin nasıl uygulanacağı hakkında yönergeler sağlar.  
  
 [Nasıl yapılır: Eski Dil Hizmetinde Genişletilmiş Ana Hat Oluşturma Desteği Sağlama](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 *Tanımlara göre Daralt* komutunu desteklemeye daha fazla dil için anahat desteğini genişleten iki seçeneği açıklar.
