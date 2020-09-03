---
title: Eski dil hizmetine genel bakış | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707355"
---
# <a name="legacy-language-service-overview"></a>Eski Dil Hizmetine Genel Bakış
Dil hizmeti, belirli özellikleri uygulamanıza olanak sağlayan düzenleyici desteği sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Yönetilen paket çerçevesi (MPF) dil hizmeti sınıfları, sık kullanılan özellikler ve diğer özellikler için kısmi destek için tam destek sağlar.

## <a name="fully-supported-features-in-the-mpf"></a>MPF 'de tam olarak desteklenen özellikler
 MPF dil hizmeti sınıfları aşağıdaki özellikleri destekler:

- Söz dizimi vurgulama

- Anahat Oluşturma

- Kod blokları açıklama oluşturma

- Ayraç eşleştirme

- Kod parçacıkları

- Özel belge özellikleri

- IntelliSense parametre bilgileri

- IntelliSense hızlı bilgi

- IntelliSense üye Tamamlama

- IntelliSense sözcük tamamlama

## <a name="partially-supported-features-in-the-mpf"></a>MPF 'de kısmen desteklenen özellikler
 MPF aşağıdaki özellikler için yalnızca kısmi destek sağlar. Bu, MPF tarafından çağrılan yöntemleri uygulamanız gerektiği anlamına gelir.

- Kodu yeniden biçimlendirme. Yeniden biçimlendirmeyi uygulayan kodu sağlarsınız.

- Geçerli kod yayılmalarını tanımlayarak kesme noktaları doğrulanıyor. Kod yayılma alanlarını tanımlayan kodu sağlarsınız.

- Değişkenleri görüntülemek için hata ayıklayıcı **oto** penceresini destekleme. Pencerede neyin gösterileceğini belirleyen kodu sağlarsınız.

- Türler ve Üyeler arasında hızlı gezinme için **Gezinti çubuğunu** destekleme. **Gezinti çubuğu** Birleşik giriş kutularındaki listeleri dolduran bir yardımcı sınıfı uygular ve döndürür.

## <a name="implementation"></a>Uygulama
 Dil hizmetinin kendisini ve diliniz için desteklemek istediğiniz dil hizmeti özelliklerini uygulamak için birkaç adımı tamamlamalısınız. Bu adımlar aşağıdaki konularda ele alınmıştır:

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
