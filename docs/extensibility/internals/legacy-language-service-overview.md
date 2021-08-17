---
title: Eski Dil Hizmetine Genel Bakış | Microsoft Docs
description: Visual Studio'daki eski dil hizmetleri ve Yönetilen Paket Çerçevesi (MPF) dil hizmeti sınıfları tarafından desteklenen özellikler hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2f6125cdbf95eec8fd329830d3465915d39b8caf0ce99fb23d3618657293592e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375720"
---
# <a name="legacy-language-service-overview"></a>Eski Dil Hizmetine Genel Bakış
Dil hizmeti, belirli özellikleri uygulamana olanak sağlayan düzenleyici desteği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sağlar. Yönetilen Paket Çerçevesi (MPF) dil hizmeti sınıfları, sık kullanılan özellikler için tam destek ve diğer özellikler için kısmi destek sağlar.

## <a name="fully-supported-features-in-the-mpf"></a>MPF'de Tam Olarak Desteklenen Özellikler
 MPF dil hizmeti sınıfları aşağıdaki özellikleri destekler:

- Söz dizimi vurgulama

- Anahat Oluşturma

- Kod bloklarını açıklamaya alma

- Küme ayracı eşleştirme

- Kod parçacıkları

- Özel belge özellikleri

- IntelliSense parametre bilgileri

- IntelliSense Hızlı Bilgileri

- IntelliSense üye tamamlama

- IntelliSense sözcük tamamlama

## <a name="partially-supported-features-in-the-mpf"></a>MPF'de Kısmen Desteklenen Özellikler
 MPF aşağıdaki özellikler için yalnızca kısmi destek sağlar. Bu, MPF tarafından çağrılan yöntemleri uygulamanın gerekli olduğu anlamına gelir.

- Kodu yeniden düzenleme. Yeniden düzenlemeyi uygulayan kodu sağlarsiniz.

- Geçerli kod aralıklarını belirleyerek kesme noktaları doğrulama. Kod aralıklarını tanımlayan kodu sağlarsiniz.

- Değişkenleri görüntülemek için hata **ayıklayıcı Otomatikleri** penceresini destekleme. Pencerede nelerin göster gösternsin, belirleyen kodu sağlarsınız.

- Türler ve **üyeler arasında** hızlı gezinti için Gezinti çubuğunu destekleme. Gezinti çubuğu birleşik giriş kutularında listeleri doldurmak için bir yardımcı sınıf **uygulayan ve** geri dönersiniz.

## <a name="implementation"></a>Uygulama
 Dil hizmetinin kendisini ve diliniz için desteklemek istediğiniz dil hizmeti özelliklerini uygulamak için birkaç adımı tamamlamanız gerekir. Bu adımlar aşağıdaki konularda ele alınmıştır:

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Ana Hat Oluşturma](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Koda Açıklama Ekleme](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Özel Belge Özellikleri](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Kod Parçacıkları için Destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Gezinti Çubuğu için Destek](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Sözcük Tamamlama](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Üye Tamamlama](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Parametre Bilgileri](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Eski Dil Hizmetinde Hızlı Bilgiler](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Kesme Noktalarını Doğrulama](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Eski Dil Hizmeti Genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md)
