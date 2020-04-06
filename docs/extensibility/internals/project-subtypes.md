---
title: Proje Alt Türleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71dab4767c806b44cbd1f9638738b4a13d6b2bcb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706404"
---
# <a name="project-subtypes"></a>Proje Alt Türleri
Proje alt türleri, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]proje sistemlerinin davranışını özelleştirmenize veya tatlandırıcınıza izin verir. Özelleştirmeler, proje dosyasına ek veri kaydetmeyi, **Yeni Öğe Ekle** iletişim kutusuna öğeleri eklemeyi veya filtrelemeyi, derlemelerin nasıl debugged ve dağıtılmadığını denetlemeyi ve proje Özellik **Sayfaları** iletişim kutusunu genişletmeyi içerir. VSPackages, COM toplama yı kullanarak proje alt türlerini uygular.

> [!NOTE]
> Visual C++ proje sistemi proje alt türlerini desteklemez. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kendisi SQL Server ve Smart Device projelerini uygulamak için proje alt türlerini kullanır.

## <a name="in-this-section"></a>Bu Bölümde
- [Proje Alt Türleri Tasarımı](../../extensibility/internals/project-subtypes-design.md)

 Proje alt türleri kavramını açıklar.

- [Proje Alt Türlerinin Başlatılma Sırası](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Programlı proje alt türü başlatma [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sırasını ortama göre açıklar.

- [Proje Alt Türleri Tarafından Genişletilen Özellikler ve Metotlar](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Proje alt türlerini kullanarak en sık genişletilmiş özelliklerin ve yöntemlerin ayrıntılı açıklamalarını sağlar.

- [MSBuild Proje Dosyasında Verileri Kalıcı Hale Getirme](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Proje dosyasındaki verilerin nasıl kalıcı yayıltığına ve proje alt türü toplama düzeyleri arasında proje dosyasındaki verileri korumak için nasıl kullanılacağını <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> açıklar.

- [Proje Özelliği Kullanıcı Arabirimi](../../extensibility/internals/project-property-user-interface.md)

 Proje alt türlerinin proje **Özellik Sayfaları** iletişim kutusunu nasıl değiştirebileceğini açıklar.

- [Temel Projenin Nesne Modelini Genişletme](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Proje alt türlerinin otomasyon nesnesi modelini genişletmek için Otomasyon Genişleticiler'i nasıl kullanabileceği hakkında bilgi sağlar.

- [Yeni Öğe Ekleme İletişim Kutusuna Katkıda Bulunma](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 **Yeni Öğe Ekle** iletişim kutusuna nasıl öğe ekleyeceğiniaçıklar.

- [Proje Dosyalarında Verileri Kaydetme](../../extensibility/saving-data-in-project-files.md)

 Yönetilen Paket Çerçevesi (MPF) kullanarak proje alt türünün proje dosyasında alt türe özgü verileri nasıl kaydedip alabileceğinizi açıklar.

- [Özelleştirilmiş Dağıtım İşleme](../../extensibility/internals/handling-specialized-deployment.md)

 Arabirimi uygulayarak proje alt türlerinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> özel dağıtım davranışını nasıl sağlayabildiğini açıklar.

- [Özellik Sayfaları Ekleme ve Kaldırma](../../extensibility/adding-and-removing-property-pages.md)

 Project Designer'da özellik sayfaları eklemeyi ve kaldırmayı açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Proje Türleri](../../extensibility/internals/project-types.md)

 Projeleri ayrıntılı olarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] anlatan konulara bağlantılar sağlar.
