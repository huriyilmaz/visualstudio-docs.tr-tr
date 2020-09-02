---
title: Düzenleyicideki eski arabirimler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8483068ae03c9a57fc67b528393e5d6830c3ec33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180286"
---
# <a name="legacy-interfaces-in-the-editor"></a>Düzenleyicideki Eski Arabirimler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio düzenleyicisine eski arabirimlerden erişebilirsiniz. Visual Studio SDK, bu arabirimlerin yeni düzenleyiciyle etkileşime geçmesini sağlayan, *dolgular*olarak bilinen bağdaştırıcıları içerir. Bununla birlikte, eski kodunuzu yeni Düzenleyici API 'sini kullanmak üzere güncelleştirmenizi öneririz. Kodunuz daha iyi gerçekleştirilir ve Windows Presentation Foundation (WPF) ve Managed Extensibility Framework (MEF) gibi yeni teknolojileri kullanabilirsiniz.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Eski Kodu Düzenleyiciye Uyarlama](../extensibility/adapting-legacy-code-to-the-editor.md)|Kodunuzu yeni düzenleyiciye nasıl uyarlayabileceğinizi açıklar.|  
|[Düzenleyici Bağdaştırıcılarıyla Yeni veya Değiştirilmiş Davranış](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Düzenleyici bağdaştırıcılarının davranışının, düzenleyicinin önceki sürümlerinden nasıl farklı olduğunu açıklar.|  
|[Temel Düzenleyicinin İçinde](../extensibility/inside-the-core-editor.md)|Düzenleyicinin önceki sürümlerinin farklı bileşenlerini açıklar.|  
|[Eski API'yi Kullanarak Temel Düzenleyiciyi Başlatma](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Çekirdek düzenleyiciyi örneklemek için eski API 'nin nasıl kullanılacağını açıklar.|  
|[Düzenleyici Fabrikaları](../extensibility/editor-factories.md)|Eski API ile düzenleyici fabrikalarının nasıl kullanılacağını açıklar.|  
|[Nasıl Yapılır: Düzenleyici Dosya Türlerini Kaydetme](../extensibility/how-to-register-editor-file-types.md)|Düzenleyicinize bir dosya adı uzantısının nasıl bağlanacağını açıklar.|  
|[İzlenecek Yol: Temel Düzenleyici Oluşturma ve Düzenleyici Dosya Türü Kaydetme](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Bir çekirdek düzenleyicinin nasıl oluşturulacağını ve bir dosya adı uzantısının buna nasıl bağlanacağını açıklar.|  
|[Nasıl Yapılır: Düzenleyiciler İçin Bağlam Sağlama](../extensibility/how-to-provide-context-for-editors.md)|Düzenleyicinize yönelik bağlamın nasıl sağlanacağını açıklar.|  
|[Dil Hizmetleri ve Temel Düzenleyici](../extensibility/language-services-and-the-core-editor.md)|Dil hizmeti ve düzenleyici arasındaki etkileşimleri açıklar.|  
|[Eski API'yi Kullanarak Metin Arabelleğine Erişme](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Eski API kullanılarak metin arabelleğine nasıl erişebileceğinizi açıklar.|  
|[Eski API'yi Kullanarak Metin Görünümüne Erişme](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Eski API kullanılarak metin görünümüne nasıl erişebileceğinizi açıklar.|  
|[Eski API'yi Kullanarak Kod Penceresini Özelleştirme](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Eski API kullanılarak kod pencerelerinin nasıl özelleştirileceğini açıklar.|  
|[Eski API'yi Kullanarak Metin Katmanlarına Erişme](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Eski API kullanılarak farklı metin katmanlarına nasıl erişebileceğinizi açıklar.|  
|[Eski API ile Metin İşaretçilerini Kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)|Eski API kullanarak metin işaretlerinin nasıl ekleneceğini açıklar.|  
|[Eski API'yi Kullanarak Düzenleyici Denetimlerini ve Menüleri Özelleştirme](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Eski API kullanılarak düzenleyici denetimlerinin nasıl özelleştirileceğini açıklar.|  
|[Eski API'yi Kullanarak Geri Alma ve Yineleme](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Geri alma işlemini yönetmeyi ve eski API 'yi kullanarak yinelemeyi açıklar.|  
|[Nasıl Yapılır: Bul ve Değiştir Mekanizması Uygulama](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Bul ve Değiştir 'in eski API kullanılarak nasıl yönetileceğini açıklar.|  
|[Nasıl Yapılır: Dosya Değişiklik Bildirimlerini Gizleme](../extensibility/how-to-suppress-file-change-notifications.md)|Eski API kullanılarak dosya değişikliği bildirimlerinin nasıl bastırılacağını açıklar.|  
|[Özel Düzenleyiciler ve Tasarımcılar Oluşturma](../extensibility/creating-custom-editors-and-designers.md)|Özel düzenleyicilerin ve tasarımcıların nasıl oluşturulacağını açıklar.|  
|[Eski Dil Hizmeti Geliştirme](../extensibility/internals/developing-a-legacy-language-service.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Dil hizmeti desteği ekleyerek temel düzenleyiciye özelleştirme özellikleri sağlayan özelliklerle ilgili belgelerin bağlantılarını sağlar.|  
|[Yazı Tiplerini ve Renkleri Kullanma](../extensibility/using-fonts-and-colors.md)|Eski arabirimlerde yazı tiplerinin ve renklerin nasıl kullanılacağını açıklar.|
