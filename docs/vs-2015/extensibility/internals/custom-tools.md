---
title: Özel araçlar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 594d564cf4a18eb0b673abd9b45b7d70e20381b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196912"
---
# <a name="custom-tools"></a>Özel Araçlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*Özel araçlar* , bir aracı projedeki bir öğeyle ilişkilendirmenize ve dosyayı her kaydedildiğinde bu aracı çalıştırmanızı sağlar. Bazen *tek dosya*oluşturucuları olarak da adlandırılan bazı özel araçlar, verilerden kod üreten ve tam tersi olan çeviricileri uygulamak için sık sık kullanılır. Örneğin, tek dosya oluşturucuları [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . Settings ve. resx dosyalarından kaynak kodu oluşturur. Oluşturulan kaynak kodu. Settings ve. resx dosyalarındaki verilere kesin olarak yazılmış erişim sağlar. [!INCLUDE[csprcs](../../includes/csprcs-md.md)]Ve [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Proje türleri özel araçları destekler; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Proje türleri desteklemez. Kendi proje türleriniz, özel araçları da destekleyebilir.  
  
 Özel araçlar, arabirimini uygulayan kayıtlı bileşenlerdir `IVsSingleFileGenerator` .  
  
 Özel araçlar bir `ProjectItem` arabirim nesnesiyle ilişkilendirilir ve tasarımcılar ve düzenleyiciler gibidir. Özel bir araç, bir as girişi ile temsil edilen dosyayı alır `ProjectItem` ve dosya adı yöntemi tarafından belirtilen yeni bir dosya yazar `DefaultExtension` .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Tek Dosya Oluşturucular Ekleme](../../extensibility/internals/implementing-single-file-generators.md)  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Özel bir araç uygulamak için arabirimin nasıl kullanılacağını açıklar.  
  
 [Projenin varsayılan ad alanını belirleme](../../misc/determining-the-default-namespace-of-a-project.md)  
 Kullanılan dile göre doğru ad alanının nasıl belirleneceğini açıklar.  
  
 [Tek Dosya Oluşturucuları Kaydetme](../../extensibility/internals/registering-single-file-generators.md)  
 Özel bir araç için tüm kayıt defteri girdilerinin açıklamalarını sağlar.  
  
 [Türleri Görsel Tasarımcıların Kullanımına Sunma](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Proje sistemlerinin, geçici Taşınabilir çalıştırılabilir (PE) dosyaları aracılığıyla oluşturulan sınıflara ve türlere erişmek için görsel tasarımcılara nasıl destek sağladığını açıklar.  
  
 [Proje Öğesinin Özelliğini Kalıcı Yapma](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Proje dosyasında, kaynak dosyanın yazarı gibi bir proje öğesi özelliğinin nasıl kalıcı yapılacağını gösterir.  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Tek bir giriş dosyasını, derlenen veya bir projeye eklenebilen tek bir çıkış dosyasına dönüştüren ile ilgili ayrıntıları sağlar.  
  
 <xref:EnvDTE.ProjectItem>  
 `ProjectItem`Bir projedeki bir öğeyi temsil eden arabirimini açıklar.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 `DefaultExtension`Çıkış dosyası adına verilen dosya adı uzantısını alan yöntemiyle ilgili ayrıntıları sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Projeleri Genişletme](../../extensibility/extending-projects.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Kod dosyalarını ve kaynak dosyalarını düzenlemek için projelerin ve çözümlerin nasıl kullanılacağını ve kaynak denetiminin nasıl uygulanacağını açıklar.
