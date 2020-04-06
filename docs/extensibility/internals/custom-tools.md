---
title: Özel Araçlar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708955"
---
# <a name="custom-tools"></a>Özel araçlar
*Özel araçlar,* bir aracı projedeki bir öğeyle ilişkilendirmenize ve dosya kaydedildiğinde bu aracı çalıştırmanıza izin sağlar. Bazen *tek dosyalı jeneratörler*olarak da adlandırılan bazı özel araçlar, verilerden kod üreten çevirmenleri uygulamak için sıklıkla kullanılır ve bunun tersi de kullanılır. Örneğin, tek dosyalı jeneratörler [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .settings ve [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] *.resx* dosyalarının dışında kod oluşturur ve kaynak oluşturur. *.settings* Oluşturulan kaynak kodu *,.settings* ve *.resx* dosyalarındaki verilere güçlü bir şekilde daktio erişim sağlar. Ve [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proje türleri özel araçları destekler; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proje türleri yok. Kendi proje türleri de özel araçları destekleyebilir.

 Özel araçlar, arabirimi `IVsSingleFileGenerator` uygulayan kayıtlı bileşenlerdir.

 Özel araçlar bir `ProjectItem` arabirim nesnesi ile ilişkilidir ve tasarımcılar ve düzenleyiciler gibidir. Özel bir araç, bir `ProjectItem` giriş olarak temsil edilen dosyayı alır ve dosya `DefaultExtension` adı yöntem tarafından sağlanan yeni bir dosya yazar.

## <a name="in-this-section"></a>Bu bölümde
- [Tek dosyalı jeneratörleri uygulama](../../extensibility/internals/implementing-single-file-generators.md)

 Özel bir aracı <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> uygulamak için arabirimin nasıl kullanılacağını açıklar.

- [Tek dosya jeneratörlerini kaydetme](../../extensibility/internals/registering-single-file-generators.md)

 Özel bir araç için tüm kayıt defteri girişleri için açıklamalar sağlar.

- [Türleri görsel tasarımcılara gösterin](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Proje sistemlerinin, geçici taşınabilir yürütülebilir (PE) dosyalar aracılığıyla oluşturulan sınıflara ve türlere erişmek için görsel tasarımcılara nasıl destek sağladığını açıklar.

- [Proje öğesinin özelliğini devam etti](../../extensibility/persisting-the-property-of-a-project-item.md)

 Proje dosyasında kaynak dosyanın yazarı gibi bir proje öğesi özelliğinin nasıl kalıcı olacağını gösterir.

## <a name="reference"></a>Başvuru
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Tek bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>giriş dosyasını derlenebilir veya projeye eklenebilen tek bir çıktı dosyasına dönüştüren , ilgili ayrıntıları sağlar.

 <xref:EnvDTE.ProjectItem>Projedeki `ProjectItem` bir öğeyi temsil eden arabirimi açıklar.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>Çıktı dosyası `DefaultExtension` adına verilen dosya adı uzantısını alan yöntem hakkında ayrıntılı bilgi sağlar.

## <a name="related-sections"></a>İlgili bölümler
- [Projeleri genişletme](../../extensibility/extending-projects.md)

 Kod dosyalarını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve kaynak dosyalarını düzenlemek için projelerin ve çözümlerin nasıl kullanılacağını ve kaynak denetiminin nasıl uygulanacağını açıklar.
