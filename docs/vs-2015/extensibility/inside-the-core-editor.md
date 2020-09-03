---
title: Çekirdek düzenleyicinin içinde | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203948"
---
# <a name="inside-the-core-editor"></a>Temel Düzenleyicinin İçinde
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Çekirdek Düzenleyici, metin bilgilerini değiştirmenize ve sorgulamanızı sağlayan birkaç bileşen kümesidir. Çekirdek düzenleyiciyi eski API kullanarak özelleştirdiyseniz, bu özelleştirmeleri kullanmaya devam edebilirsiniz, bu da düzenleyici bağdaştırıcıları aracılığıyla yönlendirilir. Ancak özelleştirmelerinizi yeni Düzenleyici API 'sine uyarlamanız önerilir.  
  
 Aşağıdaki alanlarda temel düzenleyicinin bazı önemli yönleri verilmiştir:  
  
- Metin arabelleği  
  
- Metin görünümü  
  
- Kod penceresi  
  
- Metin işaretçileri  
  
- Metin Yöneticisi  
  
- Dil hizmetleriyle tümleştirme  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Eski API'yi Kullanarak Temel Düzenleyiciyi Başlatma](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>Temel düzenleyicinin bir örneğini oluşturmak için kullanımı hakkında adım adım yönergeler sağlar.  
  
 [Eski API'yi Kullanarak Metin Arabelleğine Erişme](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Çekirdek düzenleyicide metin arabelleğinin rolünü açıklar, arabelleğe erişmek için kullanılan ilgili sistemleri açıklar ve metin arabelleği nesnesi tarafından uygulanan arabirimlerin bir listesini sağlar <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 [Eski API'deki Metin Arabelleği Olayları](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Metin arabelleği olaylarının bildirilmesi için kullanılan arabirimlerin bir listesini sağlar.  
  
 [Nasıl Yapılır: Eski API ile Metin Arabelleği Olaylarına Kaydolma](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Metin arabelleği olaylarına nasıl öneride bulunan açıklanır.  
  
 [Genel Ayarları İzlemek İçin Metin Yöneticisini Kullanma](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Metin yöneticisinin ana düzenleyici bileşenleriyle küresel tercih bilgilerini paylaşmak için nasıl kullanıldığını ve metin Yöneticisi olaylarının bildirimini nasıl alacağınızı açıklar.  
  
 [Eski API'yi Kullanarak Metin Görünümüne Erişme](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Temel düzenleyicide metin görünümünün rolünü açıklar ve nesne tarafından uygulanan arabirimleri listeler <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 [Eski API'yi Kullanarak Kod Penceresini Özelleştirme](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Bir kod penceresinin metin görünümünü çevrelemek için nasıl kullanıldığı hakkında bilgi sağlar, kod penceresine yönelik süslemeler sağlamak için kod penceresi yöneticisinin nasıl kullanıldığını açıklar ve yeni görünümler hakkında bildirim sağlar.  
  
 [Eski API'yi Kullanarak Görünüm Ayarlarını Değiştirme](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Ayarları görüntülemeyi zorlama ve zorlanan ayarları kaldırma hakkında adım adım yönergeler sağlar.  
  
 [Dil Hizmetleri ve Temel Düzenleyici](../extensibility/language-services-and-the-core-editor.md)  
 Kod süslemelerini denetlemek için bir dil hizmetinin örneklenmesini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [İzlenecek Yol: Temel Düzenleyici Oluşturma ve Düzenleyici Dosya Türü Kaydetme](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Yönetilen koddan çekirdek düzenleyiciyi başlatma hakkında adım adım yönergeler sağlar.  
  
 [Aşağı Açılan Çubuk](../extensibility/drop-down-bar.md)  
 Açılan çubuğun kod penceresinde nasıl kullanıldığını açıklar ve bir açılan çubuğu uyguladığınızda kullanılan arabirimleri açıklar.  
  
 [Eski API ile Metin İşaretçilerini Kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Metin işaretçileri kavramını ve bunların çekirdek düzenleyicide nasıl kullanıldığını açıklar ve Metin işaretleyicilerini erişmek ve yönetmek için kullanılan arabirimleri listeler.  
  
 [Nasıl Yapılır: Standart Metin İşaretçileri Ekleme](../extensibility/how-to-add-standard-text-markers.md)  
 Bir metin işaretçisi oluşturma ve kısayol menüsüne özel bir komut ekleme hakkında adım adım yönergeler sağlar.  
  
 [Nasıl yapılır: Özel Metin İşaretçileri Oluşturma](../extensibility/how-to-create-custom-text-markers.md)  
 Özel metin işaretleyicisi oluşturma ve işaret türünün bir hizmet olarak nasıl sağlanması hakkında adım adım yönergeler sağlar.
