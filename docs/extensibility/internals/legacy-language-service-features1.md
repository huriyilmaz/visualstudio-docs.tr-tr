---
title: Eski Dil Hizmeti Özellikleri1 | Microsoft Docs
description: Yönetilen paket Visual Studio (MPF) dil hizmetlerinde desteklenen temel özellikler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 94099df26da9d9fcd62db62ad440820056775a81
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626121"
---
# <a name="legacy-language-service-features-1"></a>Eski dil hizmeti özellikleri 1
Yönetilen paket çerçevesi (MPF) dil hizmeti söz dizimi vurgulama, IntelliSense ve kesme noktası doğrulaması gibi bir veya [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] daha fazla özelliği desteklemektedir. Her özellik diğer özelliklerden bağımsız olarak uygulansa da, söz dizimi vurgulaması dışında yalnızca bir tarayıcı gerektiren bir ayrıştırıcı ve tarayıcı gerekir.

## <a name="in-this-section"></a>Bu Bölümde
- [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Küme ayracı eşleştirme olarak da bilinen dil çifti eşleştirmeyi desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Koda Açıklama Ekleme](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Seçili kodun yorumunu ve açıklamalarını geri alma desteği için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Özel Belge Özellikleri](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Bir kaynak dosyaya eklenmiş belge özelliklerini desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Ana Hat Oluşturma](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Gizli bölgelerin uygulanmasıyla genel açıklamayı desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Yeniden düzenleme kodunu desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Kod Parçacıkları için Destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Eklenen ve düzenlenebilir kod parçaları olan kod parçacıklarını desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Parametre Bilgileri](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Yöntem yazıldı olarak bir yöntem imzasını görüntülemek için IntelliSense Parametre Bilgisi işlemi desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Hızlı Bilgiler](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Bir tanımlayıcı hakkında bilgi görüntülemek için IntelliSense Hızlı Bilgi işlemi desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Üye Tamamlama](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Bir ad alanının bir üyesini listeden seçmek için IntelliSense Üye Tamamlama işlemi desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Sözcük Tamamlama](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Kısmen türe sahip sözcükleri tamamlamak için IntelliSense Tam Sözcük İşlemini desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Hata ayıklama sırasında bir dil hizmetinin Otomatikler penceresini **desteklemek** için neler yapalarını açıklar.

- [Eski Dil Hizmetinde Gezinti Çubuğu için Destek](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Bu görünümde gösterilen **dosyada herhangi** bir türe veya üyeye hızlı gezinti sağlamak için düzenleyici görünümünün üst kısmında Gezinti çubuğunun nasıl kullanılası açıklanacak.

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Kaynak kodun söz dizimi vurgulamayı desteklemek için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmetinde Kesme Noktalarını Doğrulama](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Bir dil hizmetinin hata ayıklayıcı dışındaki kesme noktaları doğrulamayı desteklemek için neler yapalarını açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Yönetilen paket çerçevesini kullanan bir dil hizmetinin tüm özelliklerini uygulamak için gereken ayrıştırıcıyı ve tarayıcıyı açıklar.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 MPF kullanarak bir dil hizmetini uygulamak için nelerin gerekli olduğunu açıklar.

- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)

 MPF tabanlı bir dil hizmetini ile kaydetmek için gereken adımları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] açıklar.

- [IntelliSense'i kullanma](../../ide/using-intellisense.md)

 IntelliSense'in dil başvurularını nasıl kolay erişime neden olduğunu açıklar.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Yönetilen kodda tam özellikli bir dil hizmeti uygulamak için yönetilen paket çerçevesini (MPF) kullanma hakkında bilgi sağlar.
