---
title: Eski Dil Hizmetine Genel Bakış | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707355"
---
# <a name="legacy-language-service-overview"></a>Eski Dil Hizmetine Genel Bakış
Dil hizmeti, belirli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] özellikleri uygulamanıza olanak tanıyan düzenleyici desteği sağlar. Yönetilen Paket Çerçevesi (MPF) dil hizmeti sınıfları, sık kullanılan özellikler için tam destek ve diğer özellikler için kısmi destek sağlar.

## <a name="fully-supported-features-in-the-mpf"></a>MPF'de Tam Desteklenen Özellikler
 MPF dil hizmeti sınıfları aşağıdaki özellikleri destekler:

- Sözdizimi vurgulama

- Anahat Oluşturma

- Açıklama kod blokları

- Ayraç eşleştirme

- Kod parçacıkları

- Özel belge özellikleri

- IntelliSense parametre bilgileri

- IntelliSense Hızlı Bilgi

- IntelliSense üye tamamlama

- IntelliSense kelime tamamlama

## <a name="partially-supported-features-in-the-mpf"></a>MPF'de Kısmen Desteklenen Özellikler
 MPF, aşağıdaki özellikler için yalnızca kısmi destek sağlar. Bu, MPF tarafından çağrılan yöntemleri uygulamanız gerektiği anlamına gelir.

- Kodu yeniden biçimlendirme. Yeniden biçimlendirmeyi uygulayan kodu siz sağlıyorsunuz.

- Geçerli kod açıklıklarını tanımlayarak kesme noktalarını doğrulayın. Kod yayılmalarını tanımlayan kodu siz sağlıyorsunuz.

- Değişkenleri görüntülemek için hata ayıklama **Autos** penceresini destekleme. Pencerede ne gösterilenleri belirleyen kodu siz sağlıyorsunuz.

- Türleri ve üyeleri arasında hızlı gezinme için **Gezinti çubuğunu** destekleme. **Gezinti çubuğu** açılan kutularındaki listeleri dolduran bir yardımcı sınıf uygular ve döndürün.

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

- [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Sözcük Tamamlama](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Üye Tamamlama](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Parametre Bilgileri](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Eski Dil Hizmetinde Hızlı Bilgiler](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Eski Dil Hizmetinde Kesme Noktalarını Doğrulama](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Eski Dil Hizmeti Genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md)
