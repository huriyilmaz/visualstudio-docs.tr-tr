---
title: Eski dil Service1 uygulama | Microsoft Docs
description: Yönetilen paket çerçevesini (MPF) kullanarak genişletilmiş dil hizmeti özelliklerini destekleyen eski bir dil hizmetini nasıl uygulayacağınızı öğrenin. Bölüm 1/2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: da7e2e78013b76045c162c95f9bad9ee78b1790b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725773"
---
# <a name="implementing-a-legacy-language-service-1"></a>Eski dil hizmeti 1 uygulama
Sözdizimi vurgulama, küme ayracı eşleştirme ve IntelliSense tamamlama gibi çok çeşitli özellikleri destekleyen eski bir dil hizmetini uygulamak için yönetilen paket çerçevesi 'nde (MPF) sınıfları kullanabilirsiniz.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Dil hizmeti uygulama hakkında daha fazla bilgi edinmek için bkz. [Düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="in-this-section"></a>Bu Bölümde
- [Eski Dil Hizmetine Genel Bakış](../../extensibility/internals/legacy-language-service-overview.md)

 MPF 'de desteklenen dil hizmeti özelliklerine genel bakış.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 MPF kullanarak bir dil hizmetini uygulamak için gerekenleri açıklar.

- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)

 İle MPF tabanlı dil hizmeti kaydetmek için gereken adımları açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 MPF kullanarak bir dil hizmetinin tüm özelliklerini uygulamak için gereken iki ayrıştırıcıları açıklar.

- [İzlenecek yol: Eski Dil Hizmeti oluşturma](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Bir VSPackage içinde MPF dil hizmeti uygulamak için gereken temel adımları sağlar.

- [İzlenecek yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Yüklü kod parçacıklarının listesini alma tekniklerini gösterir.

- [Eski Dil Hizmeti Özellikleri](../../extensibility/internals/legacy-language-service-features1.md)

 MPF kullanarak bir dil hizmetinin tüm özelliklerini uygulamak için ne yapılması gerektiğini ayrıntılarıyla belirten konuların bağlantılarını sağlar.
