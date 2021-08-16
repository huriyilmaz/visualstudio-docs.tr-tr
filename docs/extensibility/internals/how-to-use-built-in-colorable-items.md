---
title: 'Nasıl yapılır: Built-In Renklenebilir öğeleri kullanma | Microsoft Docs'
description: dil hizmetiniz için Visual Studio tümleşik geliştirme ortamında (ıde) yerleşik renklenebilir öğeleri nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: ea6982d854380b8722e395db11f2ac5099a9bc26dd972ea0730cfbfeef586303
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388675"
---
# <a name="how-to-use-built-in-colorable-items"></a>Nasıl yapılır: yerleşik renklenebilir öğeleri kullanma
Yerleşik renklenebilir öğeleri kullanmadan önce, kendi özel renksiz öğelerinizi sağlamaktan önce tümleşik geliştirme ortamına (IDE) işaret etmeniz gerekir ve bu durumda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> nesneler olur. Bu, dil hizmeti için bir kayıt defteri girişi ayarlayarak yapabilirsiniz.

## <a name="to-use-built-in-colorable-items"></a>Yerleşik renklenebilir öğeleri kullanmak için

1. **HKEY_LOCAL_MACHINE\VisualStudio\\<X. Y> \Languages\Language Services \\<dil adı \>**, burada \<X.Y> bir sürümüdür [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve \<Language Name> dilinizin adıdır, **RequestStockColors** adlı bir DWORD kayıt defteri giriş değeri oluşturun.

2. **RequestStockColors** kayıt defteri girdisinin değerini *1* olarak ayarlayın.

    Kayıt defteri girişini oluşturduktan sonra, Colorizer 'ın yöntemi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> Düzenleyici tarafından kullanılacak renk öznitelikleri dizisini dolduracak şekilde numaralandırmanın üyelerini kullanabilir.

   > [!NOTE]
   > Özel renklenebilir öğeler sağlıyorsanız bu kayıt defteri girişini ayarlamayın. Daha fazla bilgi için bkz. [özel renklenebilir öğeler](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Özel düzenleyicilerde söz dizimi renklendirmesi](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Eski dil hizmetinde söz dizimi renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Sözdizimi renklendirme uygulama](../../extensibility/internals/implementing-syntax-coloring.md)
- [Özel renklenebilir öğeler](../../extensibility/internals/custom-colorable-items.md)
- [Eski dil hizmetini Kaydet](../../extensibility/internals/registering-a-legacy-language-service2.md)
