---
title: Eski dil hizmeti geliştirme | Microsoft Docs
description: eski dil hizmetini vspackage 'un bir parçası olarak veya Managed Extensibility Framework (MEF) uzantılarını kullanarak uygulama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4b300756334a84dd2e3d6ade83cc48caa10349bf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124626"
---
# <a name="develop-a-legacy-language-service"></a>Eski dil hizmeti geliştirme
Bu bölüm, eski dil hizmeti oluşturmanıza yardımcı olan konulara bağlantı sağlar.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Dil hizmeti uygulama hakkında daha fazla bilgi edinmek için bkz. [Düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="in-this-section"></a>Bu bölümde
- [Eski dil hizmeti modeli](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Çekirdek Düzenleyici için en düşük dil hizmetinin bir modelini sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu modeli, kendi dil hizmetinizi oluşturmak için bir kılavuz olarak kullanabilirsiniz.

- [Eski dil hizmeti arabirimleri](../../extensibility/internals/legacy-language-service-interfaces.md)

 Bir dil hizmetini uygulamak için gereken nesneleri açıklar ve söz dizimi vurgulaması, yöntem verileri ve diğer özellikleri sağlamak için kullanabileceğiniz ek nesnelerin bir listesini sağlar.

- [Eski dil hizmeti komutlarını kesme](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Metin görünümünün daha sonra işleyeceği komutları ele almak için dil hizmetinize bir komut filtresi eklemeyi açıklar.

- [Eski dil hizmetini Kaydet](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Kullanarak dil hizmetinizi kaydetme hakkında bilgi sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Hata ayıklama için dil hizmeti desteği](../../extensibility/internals/language-service-support-for-debugging.md)

 Bir dil hizmetinin bir hata ayıklayıcıyı desteklemek için nasıl özellik sağlayabileceğinizi açıklar.

- [Denetim listesi: eski dil hizmeti oluşturma](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Çekirdek Düzenleyici için dil hizmeti oluşturmak ve tümleştirmek için adım adım yönergeler sağlar.

## <a name="related-sections"></a>İlgili bölümler
- [Eski dil hizmetinde söz dizimi renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Dil hizmetinize nasıl sözdizimi vurgulamanın uygulanacağını açıklar.

- [Eski dil hizmetinde deyimin tamamlanması](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Bir dil hizmetinin, kullanıcıların yazmaya başladıkları bir dil anahtar sözcüğünü veya öğesini bitirmesini yardım eden işlem olan deyimin tamamlanmasını açıklar.

- [Eski dil hizmetindeki parametre bilgisi](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Aşırı yüklenmiş işlevler ve yöntemler için nasıl Yöntem ipuçları sağlayabileceğinizi açıklar.

- [Nasıl yapılır: eski dil hizmetinde gizli metin desteği sağlama](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Gizli bir metin bölgesinin amacını açıklar ve gizli metin bölgesinin nasıl uygulanacağı hakkında yönergeler sağlar.

- [Nasıl yapılır: eski dil hizmetinde genişletilmiş anahat desteği sağlama](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 *Tanımlara göre Daralt* komutunu desteklemeye daha fazla dil için anahat desteğini genişleten iki seçeneği açıklar.
