---
title: Project Alt türler | Microsoft Docs
description: Proje alt türleri Visual Studio proje sistemlerinin davranışını özelleştirmenize nasıl olanak sağladığını öğrenin. VSPackages, COM toplamasını kullanarak proje alt türlerini uygular.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: baf3502764830d088415174032a1d892632ba27d4df5f6dab793b6e4e5674ef6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121238443"
---
# <a name="project-subtypes"></a>Proje Alt Türleri
Project alt türleri, proje sistemlerinin davranışını özelleştirmenize veya değiştirmenize olanak sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Özelleştirmeler, proje dosyasına ek verilerin kaydedilmesini, **Yeni öğe Ekle** iletişim kutusunda öğe ekleyerek veya filtrelemeye, derlemelerin nasıl ayıklanmadığını ve dağıtıldığını denetlemesini ve proje **Özellik sayfaları** iletişim kutusunu genişletmeyi içerir. VSPackages, COM toplamasını kullanarak proje alt türlerini uygular.

> [!NOTE]
> Visual C++ proje sistemi proje alt türlerini desteklemiyor. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], SQL Server ve akıllı cihaz projelerini uygulamak için proje alt türlerini kullanır.

## <a name="in-this-section"></a>Bu Bölümde

- [Proje Alt Türleri Tasarımı](../../extensibility/internals/project-subtypes-design.md)

  Proje alt türleri kavramını açıklar.

- [Proje Alt Türlerinin Başlatılma Sırası](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  Ortama göre programlı proje alt türü başlatma sırasını açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Proje Alt Türleri Tarafından Genişletilen Özellikler ve Metotlar](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  Proje alt türleri kullanılarak en sık genişletilmiş özellikler ve yöntemlerin ayrıntılı açıklamalarını sağlar.

- [MSBuild Proje Dosyasında Verileri Kalıcı Hale Getirme](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  Bir proje dosyasında verilerin nasıl kalıcı yapılacağını ve proje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> dosyasındaki verileri proje alt türü toplama düzeylerinde korumak için nasıl kullanılacağını açıklar.

- [Proje Özelliği Kullanıcı Arabirimi](../../extensibility/internals/project-property-user-interface.md)

  Proje alt türlerinden proje **Özellik sayfaları** iletişim kutusunu nasıl değiştirebileceğinizi açıklar.

- [Temel Projenin Nesne Modelini Genişletme](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  Otomasyon nesne modelini genişletmek için proje alt türleri 'nin Otomasyon Genişleticilerini nasıl kullanabileceği hakkında bilgi sağlar.

- [Yeni Öğe Ekleme İletişim Kutusuna Katkıda Bulunma](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  **Yeni öğe Ekle** iletişim kutusuna öğelerin nasıl ekleneceğini açıklar.

- [Proje Dosyalarında Verileri Kaydetme](../../extensibility/saving-data-in-project-files.md)

  Proje alt türünün, yönetilen paket çerçevesi 'ni (MPF) kullanarak proje dosyasındaki alt türe özgü verileri nasıl kaydedebileceğini ve alabileceğini açıklar.

- [Özelleştirilmiş Dağıtım İşleme](../../extensibility/internals/handling-specialized-deployment.md)

  Proje alt türleri arabirimini uygulayarak nasıl özelleştirilmiş dağıtım davranışı sağlayabileceğinizi açıklar <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .

- [Özellik Sayfaları Ekleme ve Kaldırma](../../extensibility/adding-and-removing-property-pages.md)

  Project tasarımcısında özellik sayfaları ekleme ve kaldırma işlemini açıklar.

## <a name="related-sections"></a>İlgili Bölümler

- [Proje Türleri](../../extensibility/internals/project-types.md)

  Projeler hakkındaki konuların bağlantılarını sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
