---
title: Eski Dil Hizmeti1 uygulama | Microsoft Docs
description: Yönetilen paket çerçevesini (MPF) kullanarak genişletilmiş dil hizmeti özelliklerini destekleyen eski bir dil hizmetinin nasıl uygulandığını öğrenin. Bölüm 1/2.
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
ms.openlocfilehash: e7800599529157c9bcd7466f5cad21b3a826c83e371adfed9496b8b6135eca32
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121337922"
---
# <a name="implementing-a-legacy-language-service-1"></a>Eski dil hizmetini uygulama 1
Söz dizimi vurgulama, küme ayracı eşleştirme ve IntelliSense tamamlama gibi çok çeşitli özellikleri destekleyen eski bir dil hizmetini uygulamak için yönetilen paket çerçevesi (MPF) sınıflarını kullanabilirsiniz.

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Dil hizmetini uygulamanın yeni yolu hakkında daha fazla bilgi için bkz. [Düzenleyici ve Dil Hizmeti Uzantıları.](../../extensibility/editor-and-language-service-extensions.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="in-this-section"></a>Bu Bölümde
- [Eski Dil Hizmetine Genel Bakış](../../extensibility/internals/legacy-language-service-overview.md)

 MPF'de desteklenen dil hizmeti özelliklerine genel bakış.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 MPF kullanarak bir dil hizmetini uygulamak için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)

 MPF tabanlı bir dil hizmetini ile kaydetmek için gereken adımları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] açıklar.

- [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 MPF kullanarak bir dil hizmetinin tüm özelliklerini uygulamak için gereken iki ayrıştırıcıyı açıklar.

- [İzlenecek yol: Eski Dil Hizmeti oluşturma](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 VSPackage'da MPF dil hizmetini uygulamak için gereken temel adımları sağlar.

- [İzlenecek yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Yüklü kod parçacıklarının listesini alma tekniklerini gösteren.

- [Eski Dil Hizmeti Özellikleri](../../extensibility/internals/legacy-language-service-features1.md)

 MPF kullanarak bir dil hizmetinin tüm özelliklerini uygulamak için yapılması gerekenleri ayrıntılı olarak ele alan konulara bağlantılar sağlar.
