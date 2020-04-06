---
title: Editör ve Dil Hizmeti Uzantıları | Microsoft Dokümanlar
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
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712030"
---
# <a name="editor-and-language-service-extensions"></a>Editör ve dil hizmeti uzantıları
Visual Studio kod düzenleyicisinin çoğu özelliğini genişletebilirsiniz. Düzenleyici, Windows Sunu Temeli'ni (WPF) temel alınca yönetilen kodla yazılır. Bu tasarım Visual Studio'nun önceki sürümlerindeki tasarımlardan farklı olsa da, aynı özelliklerin çoğunu sağlar. Düzenleyiciyi genişletmek için Yönetilen Genişletilebilirlik Çerçevesi'ni (MEF) kullanın.

 Visual Studio SDK, önceki *sürümler* için yazılmış VSPackages'ı desteklemek için şim olarak bilinen bağdaştırıcılar sağlar. Bununla birlikte, mevcut bir VSPackage'ıniz varsa, daha iyi performans ve güvenilirlik elde etmek için yeni teknolojiye güncellemenizi öneririz.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Düzenleyici öğe şablonlarını kullanmaya giriş.|
|[Editör ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md)|Çekirdek düzenleyicinin tasarımını ve özelliklerini tanıtan ve nasıl genişletileni gösteren belgelere bağlantılar.|
|[Editörde eski arayüzler](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|Varolan koddan çekirdek düzenleyiciye nasıl erişilisin açıklayan belgelere bağlantılar.|
|[Özel editörler ve tasarımcılar oluşturun](../extensibility/creating-custom-editors-and-designers.md)|Özel düzenleyicilerin nasıl oluşturulabildiğini açıklayan belgelere bağlantılar.|
|[Eski dil hizmeti genişletilebilirlik](../extensibility/internals/legacy-language-service-extensibility.md)|Programlama dillerinin Visual Studio'ya nasıl entegre edilebildiğini açıklayan belgelere bağlantılar.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Yönetilen Genişletilebilirlik Çerçevesini (MEF) tanıtır.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Windows Sunu Temeli (WPF) tanıtır.|
