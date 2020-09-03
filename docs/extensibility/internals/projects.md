---
title: Projeler | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706210"
---
# <a name="projects"></a>Projeler
Visual Studio 'da projeler, geliştiricilerin kaynak kodu dosyalarını ve **Çözüm Gezgini**görünen diğer kaynakları düzenlemek için kullandığı kapsayıcılardır. Genellikle projeler, kaynak kodu dosyalarına ve bit eşlem dosyaları gibi kaynaklara başvuruları depolayan dosyalardır (örneğin, C# projesi için bir. csproj dosyası). Projeler, kaynak kodu, Web Hizmetleri ve veritabanlarına yönelik başvuruları ve diğer kaynakları düzenlemenize, oluşturmanıza, hata ayıklamanıza ve dağıtmanıza olanak tanır. VSPackages, Visual Studio proje sistemini üç ana şekilde genişletebilirler: *Proje türleri*, *Proje alt türleri*ve *özel araçlar*.

## <a name="in-this-section"></a>Bu Bölümde
- [Proje Türleri](../../extensibility/internals/project-types.md)

 *Proje türleri* , programlama dilleri gibi yeni proje türleri için destek ekler. Örneğin, Visual Studio 'Nun desteklediği her dilin kendi proje türü vardır ve IronPython tümleştirme örneği IronPython dili için bir proje türü içerir. Öğelerin nasıl oluşturulduğunu, ayıklanmadığını, dağıtıldığını ve **Çözüm Gezgini**görüntülendiğini özelleştirmek Için C# veya Visual Basic dışındaki diller için bir proje türü oluşturmanız gerekir. Daha fazla bilgi için bkz. [Proje türleri](../../extensibility/internals/project-types.md).

- [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)

 *Proje* alt türleri proje türlerine dayalıdır ve projelerin oluşturulduğu, hatalarının ayıklanması ve dağıtılma biçimini özelleştirmek için kullanılabilir. Visual Studio, akıllı cihaz projeleri ile proje alt türlerini kullanır; Yeni oluşturulan bir programı bir geliştirme bilgisayarından hedef cihaza kopyalayarak dağıtımı özelleştirir. C# ve Visual Basic proje türleri, proje alt türleri için temel olarak kullanılabilir; C++ proje türleri olamaz. Kendi proje türleriniz, proje alt türleri için temel olarak da kullanılabilir. Daha fazla bilgi için bkz. [Proje alt türleri](../../extensibility/internals/project-subtypes.md).

- [Web Projeleri](../../extensibility/internals/web-projects.md)

 Web uygulamasını açıklar ve bu Web uygulamaları oluşturur.

- [Yeni proje oluşturma: devlet, birinci bölüm](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) ve [Yeni proje oluşturma altında: ikinci bölüm](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Yeni bir proje oluşturduğunuzda gerçekte ne olduğunu açıklar.

- [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Proje ve çözümlerle ilgilenen VSSDK içindeki örnekleri içerir.

## <a name="related-sections"></a>İlgili Bölümler
- [Visual Studio SDK’nın İçinde](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Visual Studio genişletilebilirliğine ait farklı yönleri açıklayın.
