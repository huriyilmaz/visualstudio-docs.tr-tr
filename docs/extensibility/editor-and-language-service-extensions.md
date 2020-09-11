---
title: Düzenleyici ve dil hizmeti uzantıları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71a38d6718c22419a0a61ffbab4fe2bf6fe6c552
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012444"
---
# <a name="editor-and-language-service-extensions"></a>Düzenleyici ve dil hizmeti uzantıları
Visual Studio Code Editor özelliklerinin çoğunu genişletebilirsiniz. Düzenleyici, Windows Presentation Foundation (WPF) temel alır ve yönetilen kodda yazılmıştır. Bu tasarım, Visual Studio 'nun önceki sürümlerindeki tasarımlardan farklı olsa da, aynı özelliklerin çoğunu sağlar. Düzenleyiciyi genişletmek için Managed Extensibility Framework (MEF) kullanın.

 Visual Studio SDK, daha önceki sürümler için yazılmış VSPackages 'leri desteklemek üzere *dolgular* olarak bilinen bağdaştırıcılar sağlar. Bununla birlikte, mevcut bir VSPackage varsa, daha iyi performans ve güvenilirlik elde etmek için bunu yeni teknolojiyle güncelleştirmeniz önerilir.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Düzenleyici öğe şablonlarını kullanma konusuna giriş.|
|[Düzenleyiciyi ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md)|Temel düzenleyicinin tasarımını ve özelliklerini tanıtan ve onu genişletmeyi gösteren belgelerin bağlantıları.|
|[Düzenleyicideki eski arabirimler](../vs-2015/extensibility/legacy-interfaces-in-the-editor.md?view=vs-2015)|Mevcut koddan çekirdek düzenleyiciye nasıl erişebileceğini açıklayan belgelerin bağlantıları.|
|[Özel düzenleyiciler ve tasarımcılar oluşturma](../extensibility/creating-custom-editors-and-designers.md)|Özel düzenleyiciler oluşturmayı açıklayan belgelerin bağlantıları.|
|[Eski dil hizmeti genişletilebilirliği](../extensibility/internals/legacy-language-service-extensibility.md)|Programlama dillerinin Visual Studio 'da nasıl tümleştirileceğini betimleyen belgelerin bağlantıları.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Managed Extensibility Framework (MEF) tanıtır.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Windows Presentation Foundation (WPF) tanıtır.|