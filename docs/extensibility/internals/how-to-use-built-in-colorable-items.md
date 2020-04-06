---
title: 'Nasıl Kullanılır: Dahili Renklenebilir Öğeleri Kullanın | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707783"
---
# <a name="how-to-use-built-in-colorable-items"></a>Nasıl kullanılır: Yerleşik renklendirilebilir öğeleri kullanma
Yerleşik renklenebilir öğeleri kullanmadan önce, öncelikle tümleşik geliştirme ortamına (IDE) bu durumda nesneler olacak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> kendi özel renklenebilir öğelerinizi sağlamadığınızı belirtmelisiniz. Bunu, dil hizmeti için bir kayıt defteri girişi ayarlayarak yaparsınız.

## <a name="to-use-built-in-colorable-items"></a>Yerleşik renklendirilebilir öğeleri kullanmak için

1. **\\ HKEY_LOCAL_MACHINE\VisualStudio<X.Y>\Languages\Language\\ Services\><Language Name**altında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] X.Y \<> bir sürümü ve \<Dil Adı> dilinizin adıdır, **RequestStockColors**adlı bir DWORD kayıt defteri giriş değeri oluşturun.

2. **RequestStockColors** kayıt defteri giriş değerini *1*olarak ayarlayın.

    Kayıt defteri girişini oluşturduktan sonra, renklendiricinizin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yöntemi, <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> düzenleyici tarafından kullanılmak üzere renk öznitelikleri dizisini doldurmak için numaralandırma üyelerini kullanabilir.

   > [!NOTE]
   > Özel renklendirilebilir öğeler sağlıyorsanız bu kayıt defteri girişini ayarlamayın. Daha fazla bilgi için [bkz.](../../extensibility/internals/custom-colorable-items.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Özel editörlerde sözdizimi boyama](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Eski bir dil hizmetinde sözdizimi boyama](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Sözdizimi boyama uygulama](../../extensibility/internals/implementing-syntax-coloring.md)
- [Özel renklenebilir öğeler](../../extensibility/internals/custom-colorable-items.md)
- [Eski bir dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service2.md)
