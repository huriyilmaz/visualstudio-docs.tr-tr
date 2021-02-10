---
title: Eski dil hizmetinde sözcük tamamlama | Microsoft Docs
description: Word tamamlama, Visual Studio SDK 'daki eski dil hizmeti için desteklenebilir. Eski dil hizmetlerinin bir VSPackage içinde nasıl uygulandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3625719987afc94deda314fa61d7a8cc2c1c843
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943374"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Sözcük Tamamlama
Sözcük tamamlama, kısmen yazılmış bir sözcükteki eksik karakterleri doldurur. Yalnızca bir olası tamamlama varsa, tamamlama karakteri girildiğinde sözcük tamamlanır. Kısmi sözcük birden çok olasılığa uyuyorsa, olası tamamlamaların bir listesi görüntülenir. Bir tamamlama karakteri, tanımlayıcılar için kullanılmayan herhangi bir karakter olabilir.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementation-steps"></a>Uygulama adımları

1. Kullanıcı **IntelliSense** menüsünden **tüm sözcüğü** seçtiğinde, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> komut dil hizmetine gönderilir.

2. <xref:Microsoft.VisualStudio.Package.ViewFilter>Sınıfı komutu yakalar ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodunu ayrıştırma nedenine çağırır <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. <xref:Microsoft.VisualStudio.Package.Source>Daha sonra sınıfı, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> olası sözcük tamamlama listesini almak için yöntemini çağırır ve ardından sınıfı kullanarak bir araç ipucu listesindeki sözcükleri görüntüler <xref:Microsoft.VisualStudio.Package.CompletionSet> .

    Yalnızca bir eşleşen kelime varsa, <xref:Microsoft.VisualStudio.Package.Source> sınıf sözcüğü tamamlar.

   Alternatif olarak, <xref:Microsoft.VisualStudio.Package.TokenTriggers> bir tanımlayıcının ilk karakteri yazıldığında tarayıcı tetikleyici değerini döndürürse, <xref:Microsoft.VisualStudio.Package.Source> sınıf bunu algılar ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntemi ayrıştırma nedenine çağırır <xref:Microsoft.VisualStudio.Package.ParseReason> . Bu durumda, ayrıştırıcının bir üye seçim karakterinin varlığını algılaması ve üyelerin bir listesini sağlaması gerekir.

## <a name="enabling-support-for-the-complete-word"></a>Tüm sözcük için destek etkinleştiriliyor
 Sözcük tamamlama desteğini etkinleştirmek için, `CodeSense` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> dil paketiyle ilişkili Kullanıcı özniteliğine geçirilen adlandırılmış parametreyi ayarlayın. Bu, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> sınıfındaki özelliği ayarlar <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

 Ayrıştırmanızın <xref:Microsoft.VisualStudio.Package.ParseReason> , sözcük tamamlama işleminin çalışması için ayrıştırma nedeni değerine yanıt olarak bir bildirim listesi döndürmesi gerekir.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>ParseSource yönteminde tüm sözcüğü uygulama
 Sözcük tamamlama için, <xref:Microsoft.VisualStudio.Package.Source> sınıf, <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> olası sözcük eşleşmeleri listesini almak için sınıfındaki yöntemini çağırır. Listeyi sınıfından türetilmiş bir sınıfta uygulamanız gerekir <xref:Microsoft.VisualStudio.Package.Declarations> . <xref:Microsoft.VisualStudio.Package.Declarations>Uygulamanız gereken yöntemler hakkındaki ayrıntılar için sınıfına bakın.

 Listede yalnızca tek bir sözcük varsa, <xref:Microsoft.VisualStudio.Package.Source> sınıf otomatik olarak bu sözcüğü kısmi sözcüğün yerine ekler. Listede birden fazla sözcük varsa, <xref:Microsoft.VisualStudio.Package.Source> sınıfı kullanıcının uygun seçimi seçebileceğiniz bir araç ipucu listesi sunar.

 Ayrıca, <xref:Microsoft.VisualStudio.Package.Declarations> [eski dil hizmetinde üye tamamlandığında](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)bir sınıf uygulamasının örneğine bakın.
