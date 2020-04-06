---
title: Projeler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706210"
---
# <a name="projects"></a>Projeler
Visual Studio'da projeler, geliştiricilerin kaynak kodu dosyalarını ve **Solution Explorer'da**görünen diğer kaynakları düzenlemek için kullandıkları kapsayıcılardır. Genellikle projeler, kaynak kod dosyalarına başvuruları ve bit map dosyaları gibi kaynaklara başvuran dosyalardır (örneğin, C# projesi için .csproj dosyası). Projeler, kaynak kodu, Web hizmetleri ve veritabanlarına yapılan başvuruları ve diğer kaynakları düzenlemenize, oluşturmanıza, hata ayıklamanıza ve dağıtmanıza izin verir. VSPackages üç ana şekilde Visual Studio proje sistemi genişletebilirsiniz: *proje türleri,* *proje alt türleri,* ve *özel araçlar.*

## <a name="in-this-section"></a>Bu Bölümde
- [Proje Türleri](../../extensibility/internals/project-types.md)

 *Proje türleri,* programlama dilleri gibi yeni proje türleri için destek ekler. Örneğin, Visual Studio'nun desteklediği her dilin kendi proje türü vardır ve IronPython tümleştirme örneği IronPython dili için bir proje türü içerir. Öğelerin nasıl oluşturulup, ayıklanır, dağıtılır ve **Solution Explorer'da**görüntüleneceğini özelleştirmek için C# veya Visual Basic dışındaki diller için bir proje türü oluşturmanız gerekir. Daha fazla bilgi için [Proje Türleri'ne](../../extensibility/internals/project-types.md)bakın.

- [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)

 *Proje alt türleri* proje türlerine dayanır ve projelerin oluşturuluştürme, debugged ve dağıtılmama biçimini özelleştirmek için kullanılabilir. Visual Studio, Akıllı Cihaz projeleri ile proje alt türlerini kullanır; geliştirme bilgisayarından hedef aygıta yeni oluşturulmuş bir programı kopyalayarak dağıtımı özelleştirin. C# ve Visual Basic proje türleri proje alt türleri için temel olarak kullanılabilir; C++ proje türleri yapamaz. Kendi proje türleri de proje alt türleri için temel olarak kullanılabilir. Daha fazla bilgi için [Bkz. Proje Alt Türleri.](../../extensibility/internals/project-subtypes.md)

- [Web Projeleri](../../extensibility/internals/web-projects.md)

 Sırayla Web uygulamaları oluşturmak Web projesi açıklar.

- [Yeni Proje Üretimi: Hood altında, Bölüm Bir](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) ve [Yeni Proje Nesil: Hood altında, Bölüm İki](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Yeni bir proje oluşturduğunuzda gerçekte ne oluştuğunu açıklar.

- [VSSDK Örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples) VSSDK'da projeler ve çözümlerle ilgili örnekleri içerir.

## <a name="related-sections"></a>İlgili Bölümler
- [Visual Studio SDK’nın İçinde](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Visual Studio genişletilebilirliğinin farklı yönlerini açıklayın.
