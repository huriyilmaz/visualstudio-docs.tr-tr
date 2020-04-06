---
title: Eski Dil Hizmeti Geliştirme | Microsoft Dokümanlar
ms.date: 11/04/2016
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708665"
---
# <a name="develop-a-legacy-language-service"></a>Eski bir dil hizmeti geliştirme
Bu bölümde, eski bir dil hizmeti oluşturmanıza yardımcı olan konular bağlantı verir.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Bir dil hizmetini uygulamanın yeni yolu hakkında daha fazla bilgi edinmek için [Editör ve dil hizmeti uzantılarına](../../extensibility/editor-and-language-service-extensions.md)bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="in-this-section"></a>Bu bölümde
- [Eski bir dil hizmeti modeli](../../extensibility/internals/model-of-a-legacy-language-service.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Çekirdek düzenleyici için en az bir dil hizmeti modeli sağlar. Bu modeli kendi dil hizmetinizi oluşturmak için bir kılavuz olarak kullanabilirsiniz.

- [Eski dil hizmeti arabirimleri](../../extensibility/internals/legacy-language-service-interfaces.md)

 Bir dil hizmeti uygulamak için gereken nesneleri tartışır ve sözdizimi vurgulama, yöntem verileri ve diğer özellikleri sağlamak için kullanabileceğiniz ek nesnelerin listesini sağlar.

- [Eski dil hizmeti komutlarını engelleme](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Metin görünümünün başka şekilde işleyeceğini komutları engellemek için dil hizmetinize komut filtresi nasıl ekleyeceğiniaçıklar.

- [Eski bir dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Kullanarak dil hizmetinizi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]nasıl kaydedin izleyin

- [Hata ayıklama için dil hizmeti desteği](../../extensibility/internals/language-service-support-for-debugging.md)

 Bir dil hizmetinin hata ayıklamayı destekleyecek özellikleri nasıl sağlayabileceğini açıklar.

- [Denetim Listesi: Eski bir dil hizmeti oluşturma](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Çekirdek düzenleyici için bir dil hizmeti oluşturmak ve tümleştirmek için adım adım yönergeler sağlar.

## <a name="related-sections"></a>İlgili bölümler
- [Eski bir dil hizmetinde sözdizimi boyama](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Dil hizmetinizde sözdizimi vurgulamanın nasıl uygulanacağını tartışır.

- [Eski bir dil hizmetinde deyim tamamlama](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 İfade tamamlama, bir dil hizmetinin kullanıcıların yazmaya başladıkları bir dil anahtar sözcüklerini veya öğeyi bitirmelerine yardımcı olduğu işlemi tartışır.

- [Eski bir dil hizmetinde Parametre Bilgisi](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Aşırı yüklenen işlevler ve yöntemler için yöntem ipuçlarının nasıl sağlandığını açıklar.

- [Nasıl yapilir: Eski bir dil hizmetinde gizli metin desteği sağlayın](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Gizli metin bölgesinin amacını açıklar ve gizli metin bölgesinin nasıl uygulanacağı yla ilgili yönergeler sağlar.

- [Nasıl?](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Dillerinizin anahat *desteğini, Tanımlara Daralt* komutunu desteklemenin ötesine genişleten iki seçeneği açıklar.
