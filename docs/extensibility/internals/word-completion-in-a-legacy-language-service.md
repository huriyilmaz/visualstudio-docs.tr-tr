---
title: Eski Dil Hizmeti HizmetLerinde Sözcük Tamamlama | Microsoft Docs
description: Sözcük tamamlama, Visual Studio SDK'daki eski bir dil hizmeti için destek olabilir. Eski dil hizmetlerinin VSPackage'da nasıl uygulandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a9f32d6d99545f1daed9aed2c927c7987fe95dcd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110312"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Sözcük Tamamlama
Sözcük tamamlama, kısmen yazılmış bir sözcükteki eksik karakterleri doldurur. Yalnızca bir olası tamamlama varsa, tamamlama karakteri girilirken sözcük tamamlanır. Kısmi sözcük birden fazla olasılıkla eşleniyorsa, olası tamamlamaların listesi görüntülenir. Tamamlama karakteri, tanımlayıcılar için kullanılmadan herhangi bir karakter olabilir.

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [bkz. Düzenleyiciyi ve Dil Hizmetlerini Genişletme.](../../extensibility/extending-the-editor-and-language-services.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementation-steps"></a>Uygulama Adımları

1. Kullanıcı **IntelliSense** **menüsünden** Tam Sözcük'i seçer <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ve komut dil hizmetine gönderilir.

2. sınıfı <xref:Microsoft.VisualStudio.Package.ViewFilter> komutunu yakalar ve ayrıştırma nedeni ile yöntemini <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> çağırıyor.

3. Sınıfı daha sonra olası sözcük tamamlamalarının listesini almak için yöntemini çağırarak ve ardından sınıfını kullanarak sözcükleri <xref:Microsoft.VisualStudio.Package.Source> bir araç ipucu listesinde <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.CompletionSet> görüntüler.

    Eşleşen tek bir sözcük varsa sınıf <xref:Microsoft.VisualStudio.Package.Source> sözcüğü tamamlar.

   Alternatif olarak, bir tanımlayıcının ilk karakteri yazıldıklarında tarayıcı tetikleyici değerini döndürürse, sınıfı bunu algılar ve ayrıştırma nedeni <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source> ile yöntemini <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> arar. Bu durumda ayrıştırıcı bir üye seçimi karakterinin varlığını algılamalı ve üyelerin listesini sağla çalışmalı.

## <a name="enabling-support-for-the-complete-word"></a>Tam Sözcük Için Desteği Etkinleştirme
 Sözcük tamamlama desteğini etkinleştirmek için, dil `CodeSense` paketiyle ilişkili <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> kullanıcı özniteliğine geçirilen adlandırılmış parametreyi ayarlayın. Bu, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> sınıfındaki özelliği <xref:Microsoft.VisualStudio.Package.LanguagePreferences> ayarlar.

 Sözcük tamamlamanın çalışması için ayrıştırıcınız, ayrıştırma nedeni değerine yanıt <xref:Microsoft.VisualStudio.Package.ParseReason> olarak bildirimlerin bir listesini iade etmek zorunda.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>ParseSource Yönteminde Tam Sözcük Uygulama
 Sözcük tamamlama için, <xref:Microsoft.VisualStudio.Package.Source> sınıfı olası <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> sözcük eşleşmelerinin listesini almak için sınıfında <xref:Microsoft.VisualStudio.Package.AuthoringScope> yöntemini çağırıyor. Listesini sınıfından türetilen bir sınıfta <xref:Microsoft.VisualStudio.Package.Declarations> uygulamalı. Uygulamalı <xref:Microsoft.VisualStudio.Package.Declarations> yöntemlerle ilgili ayrıntılar için sınıfına bakın.

 Liste yalnızca tek bir sözcük içeriyorsa, sınıfı bu sözcüğü kısmi <xref:Microsoft.VisualStudio.Package.Source> sözcüğün yerine otomatik olarak ekler. Liste birden fazla sözcük içeriyorsa, sınıfı kullanıcının uygun seçimi <xref:Microsoft.VisualStudio.Package.Source> seçenin bir araç ipucu listesi sunar.

 Ayrıca Eski Dil Hizmeti'nde <xref:Microsoft.VisualStudio.Package.Declarations> Üye [Tamamlama'daki bir sınıf uygulaması örneğine de bakın.](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)
