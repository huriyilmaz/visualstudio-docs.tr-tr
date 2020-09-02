---
title: Eski dil hizmeti Features1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f2a4010529d3d9727ceb76d6a34f2cbc41b959
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238497"
---
# <a name="legacy-language-service-features-1"></a>Eski dil hizmeti özellikleri 1
Yönetilen bir paket çerçevesi (MPF) dil hizmeti, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sözdizimi vurgulama, IntelliSense ve kesme noktası doğrulaması gibi bir veya daha fazla özelliği destekleyebilir. Her özellik diğerlerinden bağımsız olarak uygulanabilir, ancak yalnızca bir tarayıcı gerektiren sözdizimi vurgulama dışında bir Ayrıştırıcı ve tarayıcı gerektirir.

## <a name="in-this-section"></a>Bu Bölümde
- [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Parantez eşleştirme olarak da bilinen dil çifti eşleşmesini desteklemek için gerekenleri açıklar.

- [Eski Dil Hizmetinde Koda Açıklama Ekleme](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Seçili kodun yorum oluşturmayı ve yorum kaldırma işlemini desteklemek için neler gerektiğini açıklar.

- [Eski Dil Hizmetinde Özel Belge Özellikleri](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Kaynak dosyaya katıştırılmış belge özelliklerini desteklemek için nelerin gerektiğini açıklar.

- [Eski Dil Hizmetinde Ana Hat Oluşturma](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Gizli bölgelerin uygulanmasıyla anahat oluşturmayı desteklemek için gerekenleri açıklar.

- [Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Yeniden biçimlendirme kodunu desteklemek için nelerin gerektiğini açıklar.

- [Eski Dil Hizmetinde Kod Parçacıkları için Destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Eklenen ve düzenlenebilen kod kesimleri olan kod parçacıklarını desteklemek için gerekenleri açıklar.

- [Eski Dil Hizmetinde Parametre Bilgileri](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Yöntem yazılırken yöntem imzasını görüntülemek için IntelliSense parametre bilgisi işlemini desteklemek için gerekenleri açıklar.

- [Eski Dil Hizmetinde Hızlı Bilgiler](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Bir tanımlayıcı hakkında bilgi görüntülemek için IntelliSense hızlı bilgi işlemini desteklemek için gerekenleri açıklar.

- [Eski Dil Hizmetinde Üye Tamamlama](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Bir listeden bir ad alanının üyesini seçmek için IntelliSense üye Tamamlama işlemini desteklemek için gerekenleri açıklar.

- [Eski Dil Hizmetinde Sözcük Tamamlama](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Kısmen yazılmış kelimeleri tamamlamak için IntelliSense 'in tüm kelime işlemini desteklemek için nelerin gerektiğini açıklar.

- [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Hata ayıklarken, bir dil hizmetinin, **oto** penceresini desteklemek için neler yapabileceğini açıklar.

- [Eski Dil Hizmetinde Gezinti Çubuğu için Destek](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Bu görünümde gösterilen dosyadaki herhangi bir tür veya üyeye hızlı bir gezinti sağlamak için düzenleyici görünümünün üst kısmında **gezinti çubuğunun** nasıl kullanılacağını açıklar.

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Kaynak kodun söz dizimi vurgulamasını desteklemek için nelerin gerektiğini açıklar.

- [Eski Dil Hizmetinde Kesme Noktalarını Doğrulama](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Bir dil hizmetinin hata ayıklayıcı dışında kesme noktalarını doğrulamayı desteklemek için neler yapabileceğini açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Yönetilen paket çerçevesini kullanan bir dil hizmetinin tüm özelliklerini uygulamak için gereken ayrıştırıcısı ve tarayıcıyı açıklar.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 MPF kullanarak bir dil hizmetini uygulamak için gerekenleri açıklar.

- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)

 İle MPF tabanlı dil hizmeti kaydetmek için gereken adımları açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [IntelliSense kullanma](../../ide/using-intellisense.md)

 IntelliSense 'in dil başvurularını erişimin kolay hale getiren açıklar.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Yönetilen kodda tam özellikli bir dil hizmeti uygulamak için yönetilen paket çerçevesi 'nin (MPF) nasıl kullanılacağı hakkında bilgi sağlar.
