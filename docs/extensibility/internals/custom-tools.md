---
title: Özel araçlar | Microsoft Docs
description: Visual Studio 'da bir aracı bir projedeki öğeyle ilişkilendiren ve dosya her kaydedildiğinde bu aracı çalıştıran özel araçlar oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7fdadad602a256b4740b4c4204704ca73864d612
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903021"
---
# <a name="custom-tools"></a>Özel araçlar
*Özel araçlar* , bir aracı projedeki bir öğeyle ilişkilendirmenize ve dosyayı her kaydedildiğinde bu aracı çalıştırmanızı sağlar. Bazen *tek dosya* oluşturucuları olarak da adlandırılan bazı özel araçlar, verilerden kod üreten ve tam tersi olan çeviricileri uygulamak için sık sık kullanılır. Örneğin, tek dosya oluşturucuları [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] *. Settings* ve *. resx* dosyalarından kaynak kodu oluşturur. Oluşturulan kaynak kodu *. Settings* ve *. resx* dosyalarındaki verilere kesin olarak yazılmış erişim sağlar. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]Ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Proje türleri özel araçları destekler; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Proje türleri desteklemez. Kendi proje türleriniz, özel araçları da destekleyebilir.

 Özel araçlar, arabirimini uygulayan kayıtlı bileşenlerdir `IVsSingleFileGenerator` .

 Özel araçlar bir `ProjectItem` arabirim nesnesiyle ilişkilendirilir ve tasarımcılar ve düzenleyiciler gibidir. Özel bir araç, bir as girişi ile temsil edilen dosyayı alır `ProjectItem` ve dosya adı yöntemi tarafından belirtilen yeni bir dosya yazar `DefaultExtension` .

## <a name="in-this-section"></a>Bu bölümde
- [Tek dosya oluşturucularını uygulama](../../extensibility/internals/implementing-single-file-generators.md)

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Özel bir araç uygulamak için arabirimin nasıl kullanılacağını açıklar.

- [Tek dosya oluşturıcıları kaydetme](../../extensibility/internals/registering-single-file-generators.md)

 Özel bir araç için tüm kayıt defteri girdilerinin açıklamalarını sağlar.

- [Türleri görsel tasarımcılara sunun](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Proje sistemlerinin, geçici Taşınabilir çalıştırılabilir (PE) dosyaları aracılığıyla oluşturulan sınıflara ve türlere erişmek için görsel tasarımcılara nasıl destek sağladığını açıklar.

- [Proje öğesinin özelliğini kalıcı hale getirme](../../extensibility/persisting-the-property-of-a-project-item.md)

 Proje dosyasında, kaynak dosyanın yazarı gibi bir proje öğesi özelliğinin nasıl kalıcı yapılacağını gösterir.

## <a name="reference"></a>Başvuru
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator><xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Tek bir giriş dosyasını, derlenen veya bir projeye eklenebilen tek bir çıkış dosyasına dönüştüren ile ilgili ayrıntıları sağlar.

 <xref:EnvDTE.ProjectItem>`ProjectItem`Bir projedeki bir öğeyi temsil eden arabirimini açıklar.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>`DefaultExtension`Çıkış dosyası adına verilen dosya adı uzantısını alan yöntemiyle ilgili ayrıntıları sağlar.

## <a name="related-sections"></a>İlgili bölümler
- [Projeleri genişletme](../../extensibility/extending-projects.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kod dosyalarını ve kaynak dosyalarını düzenlemek için projelerin ve çözümlerin nasıl kullanılacağını ve kaynak denetiminin nasıl uygulanacağını açıklar.
