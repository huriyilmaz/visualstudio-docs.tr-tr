---
title: Projeler | Microsoft Docs
description: vspackages 'ın proje türleri, proje alt türleri ve özel araçlar dahil Visual Studio proje sistemini genişletebilme yolları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2f0defdf43558cb94d3337a02d71ad768120da8c930244a9b03e1f05f6e75ee6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401290"
---
# <a name="projects"></a>Projeler
Visual Studio, projeler, geliştiricilerin kaynak kodu dosyalarını ve **Çözüm Gezgini** görünen diğer kaynakları düzenlemek için kullandığı kapsayıcılardır. Genellikle projeler, kaynak kodu dosyalarına ve bit eşlem dosyaları gibi kaynaklara başvuruları depolayan dosyalardır (örneğin, C# projesi için bir. csproj dosyası). Projeler, kaynak kodu, Web Hizmetleri ve veritabanlarına yönelik başvuruları ve diğer kaynakları düzenlemenize, oluşturmanıza, hata ayıklamanıza ve dağıtmanıza olanak tanır. vspackages Visual Studio proje sistemini üç ana şekilde genişletebilirler: *proje türleri*, proje alt *türleri* ve *özel araçlar*.

## <a name="in-this-section"></a>Bu Bölümde
- [Proje Türleri](../../extensibility/internals/project-types.md)

 *Project türler* , programlama dilleri gibi yeni proje türleri için destek ekler. örneğin, Visual Studio desteklediği her dilin kendi proje türü vardır ve ıronpython tümleştirme örneği ıronpython dili için bir proje türü içerir. öğelerin nasıl oluşturulduğunu, ayıklanmadığını, dağıtıldığını ve **Çözüm Gezgini** görüntülendiğini özelleştirmek için C# veya Visual Basic dışındaki diller için bir proje türü oluşturmanız gerekir. daha fazla bilgi için bkz. [Project türleri](../../extensibility/internals/project-types.md).

- [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)

 *Project* alt türleri proje türlerine dayalıdır ve projelerin oluşturulması, hatalarının ayıklanması ve dağıtılması biçimini özelleştirmek için kullanılabilir. Visual Studio, akıllı cihaz projeleri ile proje alt türlerini kullanır; Yeni oluşturulan bir programı bir geliştirme bilgisayarından hedef cihaza kopyalayarak dağıtımı özelleştirir. C# ve Visual Basic proje türleri, proje alt türleri için temel olarak kullanılabilir; C++ proje türleri olamaz. Kendi proje türleriniz, proje alt türleri için temel olarak da kullanılabilir. daha fazla bilgi için bkz. [Project alt türleri](../../extensibility/internals/project-subtypes.md).

- [Web Projeleri](../../extensibility/internals/web-projects.md)

 Web uygulamasını açıklar ve bu Web uygulamaları oluşturur.

- [yeni Project oluşturma: birinci bölüm bir](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) ve [yeni Project oluşturma altında: devlet, ikinci bölüm](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Yeni bir proje oluşturduğunuzda gerçekte ne olduğunu açıklar.

- [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Proje ve çözümlerle ilgilenen VSSDK içindeki örnekleri içerir.

## <a name="related-sections"></a>İlgili Bölümler
- [Visual Studio SDK’nın İçinde](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Visual Studio genişletilebilirliği farklı yönlerini açıklayın.
