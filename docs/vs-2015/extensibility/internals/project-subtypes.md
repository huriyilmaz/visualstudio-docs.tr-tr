---
title: Proje alt türleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5ad1e105d43c40782b13d8799b20626e57363c2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782444"
---
# <a name="project-subtypes"></a>Proje Alt Türleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje alt türleri, proje sistemlerinin davranışını özelleştirmenize ya da değiştirmenize olanak sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Özelleştirmeler, proje dosyasına ek verilerin kaydedilmesini, **Yeni öğe Ekle** iletişim kutusunda öğe ekleyerek veya filtrelemeye, derlemelerin nasıl ayıklanmadığını ve dağıtıldığını denetlemesini ve proje **Özellik sayfaları** iletişim kutusunu genişletmeyi içerir. VSPackages, COM toplamasını kullanarak proje alt türlerini uygular.  
  
> [!NOTE]
> Visual C++ proje sistemi proje alt türlerini desteklemiyor. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , SQL Server ve akıllı cihaz projelerini uygulamak için proje alt türlerini kullanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Proje Alt Türleri Tasarımı](../../extensibility/internals/project-subtypes-design.md)  
 Proje alt türleri kavramını açıklar.  
  
 [Proje Alt Türlerinin Başlatılma Sırası](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Ortama göre programlı proje alt türü başlatma sırasını açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Proje Alt Türleri Tarafından Genişletilen Özellikler ve Metotlar](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Proje alt türleri kullanılarak en sık genişletilmiş özellikler ve yöntemlerin ayrıntılı açıklamalarını sağlar.  
  
 [MSBuild Proje Dosyasında Verileri Kalıcı Hale Getirme](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Bir proje dosyasında verilerin nasıl kalıcı yapılacağını ve proje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> dosyasındaki verileri proje alt türü toplama düzeylerinde korumak için nasıl kullanılacağını açıklar.  
  
 [Proje Özelliği Kullanıcı Arabirimi](../../extensibility/internals/project-property-user-interface.md)  
 Proje alt türlerinden proje **Özellik sayfaları** iletişim kutusunu nasıl değiştirebileceğinizi açıklar.  
  
 [Temel Projenin Nesne Modelini Genişletme](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Otomasyon nesne modelini genişletmek için proje alt türleri 'nin Otomasyon Genişleticilerini nasıl kullanabileceği hakkında bilgi sağlar.  
  
 [Yeni Öğe Ekleme İletişim Kutusuna Katkıda Bulunma](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 **Yeni öğe Ekle** iletişim kutusuna öğelerin nasıl ekleneceğini açıklar.  
  
 [Proje Dosyalarında Verileri Kaydetme](../../extensibility/saving-data-in-project-files.md)  
 Proje alt türünün, yönetilen paket çerçevesi 'ni (MPF) kullanarak proje dosyasındaki alt türe özgü verileri nasıl kaydedebileceğini ve alabileceğini açıklar.  
  
 [Özelleştirilmiş Dağıtım İşleme](../../extensibility/internals/handling-specialized-deployment.md)  
 Proje alt türleri arabirimini uygulayarak nasıl özelleştirilmiş dağıtım davranışı sağlayabileceğinizi açıklar <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .  
  
 [Özellik Sayfaları Ekleme ve Kaldırma](../../extensibility/adding-and-removing-property-pages.md)  
 Proje tasarımcısında Özellik sayfaları ekleme ve kaldırma işlemini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Projeler hakkındaki konuların bağlantılarını sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
