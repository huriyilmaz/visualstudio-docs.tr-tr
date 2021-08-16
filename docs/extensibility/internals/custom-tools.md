---
title: Özel Araçlar | Microsoft Docs
description: Bir aracı proje içinde bir öğeyle Visual Studio ve dosya kaydedilebilirken bu aracı çalıştıran özel araçlar oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e414b8a27ee64832d13d6f4614e53131bb9bae4dd01bee63715c9c28edf5493a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359643"
---
# <a name="custom-tools"></a>Özel araçlar
*Özel araçlar,* bir aracı proje içinde bir öğeyle ilişkilendirmenizi ve dosya her kaydedilebilirken bu aracı çalıştırmanızı sağlar. Bazen tek dosya oluşturucular olarak da adlandırılan bazı özel araçlar *genellikle* verilerden kod oluşturan çevirmenleri (veya tam tersi) uygulamak için kullanılır. Örneğin, tek dosya oluşturucuları [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .settings ve  *.resx* dosyalarında kod oluşturabilir ve kaynak kodu oluşturabilir. Oluşturulan kaynak kodu, *.settings* ve *.resx* dosyalarındaki verilere kesin olarak türü kesin olarak yazarak erişim sağlar. ve [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proje türleri özel araçları [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] destekler; proje türleri [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] desteklemez. Kendi proje türleriniz özel araçları da destekleyebilirsiniz.

 Özel araçlar, arabirimi uygulayan kayıtlı `IVsSingleFileGenerator` bileşenlerdir.

 Özel araçlar bir arabirim `ProjectItem` nesnesiyle ilişkilendirilen ve tasarımcılar ve düzenleyiciler gibi. Özel bir araç, giriş olarak temsil edilen dosyayı alır ve dosya adı yöntemi tarafından sağlanan `ProjectItem` yeni bir dosya `DefaultExtension` yazar.

## <a name="in-this-section"></a>Bu bölümde
- [Tek dosya oluşturucuları uygulama](../../extensibility/internals/implementing-single-file-generators.md)

 Özel bir araç uygulamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> arabirimin nasıl kullanıldığını açıklar.

- [Tek dosya oluşturucuları kaydetme](../../extensibility/internals/registering-single-file-generators.md)

 Özel bir araç için tüm kayıt defteri girdileri için açıklamalar sağlar.

- [Türleri görsel tasarımcıların ortaya çıkarma](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Proje sistemlerinin geçici taşınabilir yürütülebilir (PE) dosyalar aracılığıyla oluşturulan sınıflara ve türlere erişmesi için görsel tasarımcıların nasıl destek sağlaycı olduğunu açıklar.

- [Proje öğesinin özelliğini kalıcı olarak kalıcı olarak](../../extensibility/persisting-the-property-of-a-project-item.md)

 Proje dosyasında bir kaynak dosyanın yazarı gibi bir proje öğesi özelliğinin nasıl kalıcı olduğunu gösterir.

## <a name="reference"></a>Başvuru
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Tek bir giriş dosyasını derlenmiş veya projeye eklen bir tek çıkış dosyasına <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> dönüştüren hakkında ayrıntılar sağlar.

 <xref:EnvDTE.ProjectItem> Proje `ProjectItem` içinde bir öğeyi temsil eden arabirimini açıklar.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> Çıkış dosyası `DefaultExtension` adına verilen dosya adı uzantısını alan yöntemi hakkında ayrıntılar sağlar.

## <a name="related-sections"></a>İlgili bölümler
- [Projeleri genişletme](../../extensibility/extending-projects.md)

 Kod dosyalarını ve kaynak dosyalarını düzenlemek için projelerin ve çözümlerin nasıl kullanıldığını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve kaynak denetimin nasıl uygulandığını açıklar.
