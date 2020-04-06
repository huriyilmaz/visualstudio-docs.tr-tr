---
title: Eski Dil Hizmeti Özellikleri1 | Microsoft Dokümanlar
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
ms.openlocfilehash: f0be7cb4401792b30eac595faf64162dc375dbb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707392"
---
# <a name="legacy-language-service-features"></a>Eski Dil Hizmeti Özellikleri
Yönetilen paket çerçevesi (MPF) dil hizmeti, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sözdizimi vurgulama, IntelliSense ve kesme noktası doğrulaması gibi bir veya daha fazla özelliği destekleyebilir. Her özellik diğerlerinden bağımsız olarak uygulanabilir, ancak yalnızca bir tarayıcı gerektiren sözdizimi vurgulama dışında bir arayış ve tarayıcı gerektirir.

## <a name="in-this-section"></a>Bu Bölümde
- [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Ayraç eşleştirmesi olarak da bilinen dil çifti eşlemi nin desteklenmesi için gerekenleri açıklar.

- [Eski Dil Hizmetinde Koda Açıklama Ekleme](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Seçili kodun yorumlanması ve yorumsuz olmasını desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Özel Belge Özellikleri](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Kaynak dosyaya katıştırılmış belge özelliklerini desteklemek için gerekenleri açıklar.

- [Eski Dil Hizmetinde Ana Hat Oluşturma](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Gizli bölgelerin uygulanması yoluyla ana hatlarıyla desteklemek için gerekenleri açıklar.

- [Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Kodu yeniden biçimlendirmeyi desteklemek için gerekenleri açıklar.

- [Eski Dil Hizmetinde Kod Parçacıkları için Destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Eklenen ve düzenlenebilecek kod bölümleri olan kod parçacıklarını desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Parametre Bilgileri](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Yöntem yazılırken yöntem imzasını görüntülemek için IntelliSense Parametre Bilgisi işlemini desteklemek için gerekenleri açıklar.

- [Eski Dil Hizmetinde Hızlı Bilgiler](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Tanımlayıcı hakkında bilgi görüntülemek için IntelliSense Hızlı Bilgi işlemini desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Üye Tamamlama](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Bir listeden bir ad alanı nın üyesini seçmek için IntelliSense Üye Tamamlama işlemini desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Sözcük Tamamlama](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Kısmen yazılan sözcükleri tamamlamak için IntelliSense Complete Word işlemini desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Hata ayıklama sırasında bir dil hizmetinin **Otomatik ler** penceresini desteklemek için neler yapabileceğini açıklar.

- [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Bu görünümde gösterilen dosyadaki herhangi bir türe veya üyeye hızlı gezinme sağlamak için düzenleyici görünümün üst kısmında **Gezinti çubuğunun** nasıl kullanılacağını açıklar...

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Kaynak kodun sözdizimi vurgulamasını desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Kesme Noktalarını Doğrulama](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Bir dil hizmetinin hata ayıklayıcı dışında kesme noktalarını doğrulamak için neler yapabileceğini açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Yönetilen paket çerçevesini kullanan bir dil hizmetinin tüm özelliklerini uygulamak için gereken ayrıştırıcıyı ve tarayıcıyı açıklar.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 MPF'yi kullanarak bir dil hizmeti uygulamak için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)

 MPF tabanlı bir dil hizmetini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [IntelliSense Kullanma](../../ide/using-intellisense.md)

 IntelliSense'in dil referanslarına erişimi nasıl kolaylaştırdığını açıklar.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Yönetilen kodda tam özellikli bir dil hizmeti uygulamak için yönetilen paket çerçevesinin (MPF) nasıl kullanılacağı hakkında bilgi sağlar.
