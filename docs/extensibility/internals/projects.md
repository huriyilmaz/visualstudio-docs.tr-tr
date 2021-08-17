---
title: Projeler | Microsoft Docs
description: VSPackage'ların proje türleri, proje alt türleri Visual Studio özel araçlar dahil olmak üzere proje sistemini genişletme yollarını öğrenin.
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
ms.openlocfilehash: 9daeac1804940eb80331461b12b2cda51e9fef55
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063024"
---
# <a name="projects"></a>Projeler
Bu Visual Studio, geliştiricilerin kaynak kodu dosyalarını ve içinde görünen diğer kaynakları düzenlemek için **Çözüm Gezgini.** Projeler genellikle kaynak kod dosyalarına ve bit eşlem dosyaları gibi kaynaklara yapılan başvuruları depolar. (Örneğin, bir C# projesi için .csproj dosyası) dosyalardır. Projeler kaynak kodunu düzenlemenize, derlemenize, hata ayıklamanızı ve dağıtmanızı, Web hizmetleri ve veritabanlarına yönelik başvuruları ve diğer kaynakları dağıtmanızı sağlar. VSPackage'lar proje Visual Studio üç ana şekilde genişletebilir: *proje türleri,* *proje alt* türleri ve *özel araçlar.*

## <a name="in-this-section"></a>Bu Bölümde
- [Proje Türleri](../../extensibility/internals/project-types.md)

 *Project türleri,* programlama dilleri gibi yeni proje türleri için destek ekler. Örneğin, Visual Studio dillerin kendi proje türü vardır ve IronPython tümleştirme örneği IronPython dili için bir proje türü içerir. Öğelerin nasıl oluşturulacak, hata ayıklanacak, dağıtılacak ve Visual Basic için C# veya **Çözüm Gezgini.** Daha fazla bilgi için [bkz. Project Türleri.](../../extensibility/internals/project-types.md)

- [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)

 *Project türler* proje türlerini temel almaktadır ve projelerin nasıl yazılacağı, hata ayıklandırılacağı ve dağıtılacağı şekilde özelleştirilebilir. Visual Studio Cihaz projeleriyle proje alt türleri kullanır; yeni oluşturulan bir programı bir geliştirme bilgisayardan hedef cihaza kopyalayıp dağıtımı özelleştirilebilir. C# ve Visual Basic proje türleri proje alt türleri için temel olarak kullanılabilir; C++ proje türleri olamaz. Kendi proje türleriniz, proje alt türleri için temel olarak da kullanılabilir. Daha fazla bilgi için [bkz. Project Alt Türleri.](../../extensibility/internals/project-subtypes.md)

- [Web Projeleri](../../extensibility/internals/web-projects.md)

 Sırasıyla Web uygulamaları oluşturan Web projesini açıklar.

- [Yeni Project Oluşturma: Başlık Altında, Bölüm Bir](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) ve [Yeni Project Oluşturma: Başlık Altında, Bölüm İki](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Yeni bir proje oluşturma sırasında gerçekten neler olduğunu açıklar.

- [VSSDK Örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples) VSSDK'de projeler ve çözümlerle ilgili örnekler içerir.

## <a name="related-sections"></a>İlgili Bölümler
- [Visual Studio SDK’nın İçinde](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Genişletilebilirlik ile ilgili Visual Studio açıklama.
