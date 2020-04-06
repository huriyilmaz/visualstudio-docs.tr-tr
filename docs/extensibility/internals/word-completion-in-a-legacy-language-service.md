---
title: Eski Dil Hizmetinde Kelime Tamamlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703169"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Sözcük Tamamlama
Sözcük tamamlama, kısmen yazılan bir sözcükteki eksik karakterleri doldurur. Yalnızca bir olası tamamlanma varsa, tamamlama karakteri girildiğinde sözcük tamamlanır. Kısmi sözcük birden fazla olasılıkla eşleşiyorsa, olası tamamlamaların listesi görüntülenir. Tamamlama karakteri tanımlayıcılar için kullanılmayan herhangi bir karakter olabilir.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [Editör ve Dil Hizmetlerini Genişletme'ye](../../extensibility/extending-the-editor-and-language-services.md)bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementation-steps"></a>Uygulama Adımları

1. Kullanıcı **IntelliSense** menüsünden **Tam Word'u** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> seçtiğinde, komut dil hizmetine gönderilir.

2. Sınıf <xref:Microsoft.VisualStudio.Package.ViewFilter> komutu yakalar ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> ayrışdırış nedeni <xref:Microsoft.VisualStudio.Package.ParseReason>ile yöntemi çağırır.

3. Sınıf <xref:Microsoft.VisualStudio.Package.Source> daha sonra <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> olası sözcük tamamlama listesini almak için yöntemi çağırır ve sonra <xref:Microsoft.VisualStudio.Package.CompletionSet> sınıfı kullanarak bir araç ipucu listesinde sözcükleri görüntüler.

    Yalnızca eşleşen bir sözcük <xref:Microsoft.VisualStudio.Package.Source> varsa, sınıf sözcüğü tamamlar.

   Alternatif olarak, bir tanımlayıcının <xref:Microsoft.VisualStudio.Package.TokenTriggers> ilk karakteri yazıldığında tarayıcı tetikleyici değerini döndürürse, <xref:Microsoft.VisualStudio.Package.Source> sınıf bunu <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> algılar ve yöntemi ayrıştırma nedeni ile <xref:Microsoft.VisualStudio.Package.ParseReason>çağırır. Bu durumda, araüye üye bir seçim karakterinin varlığını algılamalı ve üye listesini sağlamalıdır.

## <a name="enabling-support-for-the-complete-word"></a>Tam Word için Desteği Etkinleştirme
 Sözcük tamamlama desteği sağlamak `CodeSense` için, dil <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> paketiyle ilişkili kullanıcı özniteliğine geçirilen adlandırılmış parametreyi ayarlayın. Bu, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> sınıfın özelliğini <xref:Microsoft.VisualStudio.Package.LanguagePreferences> ayarlar.

 Ayrıştırıcınızın, sözcük tamamlamanın çalışması için ayrıştırıcı neden değerine <xref:Microsoft.VisualStudio.Package.ParseReason>yanıt olarak bir bildirim listesi döndürmesi gerekir.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>ParseSource Yönteminde Tam Word'ün Uygulanması
 Sözcük tamamlama <xref:Microsoft.VisualStudio.Package.Source> için sınıf, olası <xref:Microsoft.VisualStudio.Package.AuthoringScope> sözcük eşleşmelerinin listesini almak için sınıftaki <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> yöntemi çağırır. Listeyi <xref:Microsoft.VisualStudio.Package.Declarations> sınıftan türetilen bir sınıfta uygulamanız gerekir. Uygulamanız <xref:Microsoft.VisualStudio.Package.Declarations> gereken yöntemlerle ilgili ayrıntılar için sınıfa bakın.

 Liste yalnızca tek bir sözcük <xref:Microsoft.VisualStudio.Package.Source> içeriyorsa, sınıf bu sözcüğü kısmi sözcüğün yerine otomatik olarak ekler. Liste birden fazla sözcük içeriyorsa, <xref:Microsoft.VisualStudio.Package.Source> sınıf, kullanıcının uygun seçimi seçebileceği bir araç ipucu listesi sunar.

 Ayrıca, Eski Dil <xref:Microsoft.VisualStudio.Package.Declarations> [Hizmetinde Üye Tamamlama'da](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)sınıf uygulaması örneğine de bakın.
