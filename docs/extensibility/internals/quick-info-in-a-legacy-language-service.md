---
title: Eski Dil Hizmeti HizmetLerinde Hızlı Bilgi | Microsoft Docs
description: Bir tanımlayıcı hakkında bilgi görüntülemeye yönelik IntelliSense Hızlı Bilgi işlemi desteği hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d375672fa25949f85da7551a55c606d21e5c266e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636057"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Hızlı Bilgiler
IntelliSense Hızlı Bilgileri, kullanıcı tanımlayıcıya caret yerleştirerek **IntelliSense** menüsünden  Hızlı Bilgi'yi seçerek veya fare imlecini tanımlayıcının üzerinde tutarken kaynakta yer alan tanımlayıcıyla ilgili bilgileri gösterir. Bu, tanımlayıcı hakkında bilgilerle birlikte bir araç ipucu görünmesine neden olur. Bu bilgiler genellikle tanımlayıcı türünden oluşur. Hata ayıklama altyapısı etkin olduğunda, bu bilgiler geçerli değeri içerebilir. Dil hizmeti yalnızca tanımlayıcıları işlerken hata ayıklama altyapısı ifade değerleri sağlar.

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [bkz. Walkthrough: Displaying QuickInfo Tooltips](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 Yönetilen paket çerçevesi (MPF) dil hizmeti sınıfları, IntelliSense Hızlı Bilgi araç ipucu görüntülemeye tam destek sağlar. Tek gereken, görüntülenecek metni sağlamak ve hızlı bilgi özelliğini etkinleştirmektir.

 Görüntülenecek metin, ayrıştırma nedeni değeriyle <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntem ayrıştırıcısı çağrılarak elde <xref:Microsoft.VisualStudio.Package.ParseReason> edilir. Bu nedenle ayrıştırıcıya nesnede belirtilen konumdaki tanımlayıcı için tür bilgilerini (veya Hızlı Bilgi araç ipucunda görüntülenmek üzere uygun olan her şeyi) <xref:Microsoft.VisualStudio.Package.ParseRequest> almasını söyler. <xref:Microsoft.VisualStudio.Package.ParseRequest>nesnesi, yöntemine geçirilen <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> nesnedir.

 Ayrıştırıcı, tüm tanımlayıcıların türlerini belirlemek için <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnesinde konuma kadar her şeyi ayrıştırmalı. Ardından ayrıştırıcının ayrıştırma isteği konumunun tanımlayıcısını almaları gerekir. Son olarak, nesnesinin yönteminden metni geri getiremesini için ayrıştırıcının bu tanımlayıcıyla ilişkili araç ipucu <xref:Microsoft.VisualStudio.Package.AuthoringScope> verilerini nesnesine geçmesi <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> gerekir.

## <a name="enabling-the-quick-info-feature"></a>Hızlı Bilgi Özelliğini Etkinleştirme
 Hızlı Bilgi özelliğini etkinleştirmek için ve adlandırılmış `CodeSense` `QuickInfo` parametrelerini ayarlayabilirsiniz. <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Bu öznitelikler ve <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> özelliklerini <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> ayarlayın.

## <a name="implementing-the-quick-info-feature"></a>Hızlı Bilgi Özelliğini Uygulama
 sınıfı <xref:Microsoft.VisualStudio.Package.ViewFilter> IntelliSense Hızlı Bilgi işlemiyle başa çıkabilir. sınıf komutunu aldığında, sınıf ayrıştırma nedeni ve komut gönderiken caret konumu <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ile yöntemini <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> çağıran. Yöntem ayrıştırıcısı daha sonra kaynağı verilen konuma kadar ayrıştırmalı ve ardından Hızlı Bilgi araç ipucunda nelerin görüntü gerektiğini belirlemek için verilen konumdaki <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> tanımlayıcıyı ayrıştırmalıdır.

 Çoğu ayrıştırıcı, kaynak dosyanın tamamının ilk ayrıştırmasını yapar ve sonuçları ayrıştırma ağacında depolar. Yöntemine geçirilen tüm <xref:Microsoft.VisualStudio.Package.ParseReason> ayrıştırmalar <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> gerçekleştirildi. Daha sonra diğer ayrıştırma türleri istenen bilgileri almak için ayrıştırma ağacını kullanabilir.

 Örneğin, ayrıştırma nedeni değeri kaynak konumda tanımlayıcıyı bulabilir ve tür bilgilerini almak için <xref:Microsoft.VisualStudio.Package.ParseReason> ayrıştırma ağacında bu tanımlayıcıyı bulabilir. Bu tür bilgileri daha sonra <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfına geçir edilir ve yöntemi tarafından <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> döndürülür.
