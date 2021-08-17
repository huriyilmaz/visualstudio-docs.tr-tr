---
title: 'Nasıl kullanılır: Renk Built-In Öğeleri | Microsoft Docs'
description: Dil hizmetiniz için tümleşik geliştirme ortamında (IDE) yerleşik renk Visual Studio kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 903a69eb19fb0d70558302aee4ae356ee65224ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063271"
---
# <a name="how-to-use-built-in-colorable-items"></a>Nasıl kullanılır: Yerleşik renklenebilir öğeleri kullanma
Yerleşik renklenebilir öğeleri kullanmadan önce, önce tümleşik geliştirme ortamına (IDE) kendi özel renklenebilir öğelerinizi sağlamamanızı (bu durumda nesne) <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> işaretlendirmeniz gerekir. Dil hizmeti için bir kayıt defteri girişi ayarerek bunu yapacaktır.

## <a name="to-use-built-in-colorable-items"></a>Yerleşik renklenebilir öğeleri kullanmak için

1. **HKEY_LOCAL_MACHINE\VisualStudio<\\ X.Y>\Languages\Language Services \\<\> Dil** Adı altında, bir sürümüdür ve dilinizin adıdır, \<X.Y> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \<Language Name> **RequestStockColors** adlı bir DWORD kayıt defteri giriş değeri oluşturun.

2. **RequestStockColors kayıt defteri** giriş değerini *1 olarak ayarlayın.*

    Kayıt defteri girdisini oluşturdukta, renklandırıcı yönteminiz, düzenleyici tarafından kullanmak üzere renk öznitelikleri dizisini doldurmak için sabitleyicinin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> üyelerini kullanabilir.

   > [!NOTE]
   > Özel renklenebilir öğeler sağlıyorsanız bu kayıt defteri girişini ayarlayamazsanız. Daha fazla bilgi için [bkz. Özel renkleştirilebilir öğeler.](../../extensibility/internals/custom-colorable-items.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Özel düzenleyicilerde söz dizimi renklendirmesi](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Eski dil hizmetlerinde söz dizimi renklendirme](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Söz dizimi renklendirmesi uygulama](../../extensibility/internals/implementing-syntax-coloring.md)
- [Özel renkleştirilebilir öğeler](../../extensibility/internals/custom-colorable-items.md)
- [Eski dil hizmetini kaydetme](../../extensibility/internals/registering-a-legacy-language-service2.md)
