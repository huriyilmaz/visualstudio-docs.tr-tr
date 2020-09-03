---
title: Proje ve proje öğesi şablonları ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203864"
---
# <a name="adding-project-and-project-item-templates"></a>Proje ve Proje Öğesi Şablonları Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kendi proje türlerinizi oluştururken, standart [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tümleşik geliştirme ortamı (IDE) iletişim kutularını kullanarak yeni projeler ve proje öğeleri ekleme desteği sağlamanız gerekir. Aşağıdaki konularda projeler ve proje öğeleri eklemek için farklı teknikler ele alınmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Proje Bağlamı](../../extensibility/internals/project-context.md)  
 Projenin, ortamda transpires için bağlam bilgilerinin çoğunu sağladığını açıklar.  
  
 [Proje Önceliği](../../extensibility/internals/project-priority.md)  
 Öğe açmak için hangi projenin kullanıldığı hakkında belirsizliğe engel olmak için bir proje öğesinin genellikle bir projenin üyesi olduğunu açıklar.  
  
 [Çeşitli Dosyalar Projesi](../../extensibility/internals/miscellaneous-files-project.md)  
 Bir projede dosyaları açmak için kullanılabilecek iki Düzenleyici türü ve proje öğesi açıldığında hangi düzenleyicinin kullanılacağını belirlemek için projenin oynadığı rol hakkında bilgi sağlar.  
  
 [Proje ve Öğe Şablonlarını Kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)  
 Proje oluşturulduğunda ne olduğunu açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Yeni Öğe Ekleme İletişim Kutularına Öğe Ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 **Yeni öğe Ekle** iletişim kutusuna öğe ekleme işlemini açıklar.  
  
 [Yeni Proje İletişim Kutusuna Dizin Ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 VSPackage tarafından kullanılabilir hale getirilen özel şablonları içeren yeni bir dizin kaydetme örneği sağlar.  
  
 [Yeni Öğe Ekleme İletişim Kutusuna Dizin Ekleme](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 **Yeni öğe Ekle** iletişim kutusu için yeni bir dizin kümesi kaydetmenin bir örneğini sağlar.  
  
 [Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Proje sistemlerini genişletmek için kullanılan farklı komut öğesi türlerini listeler.  
  
 [Genişletme Projeleri için Genellikle Kullanılan Nesnelerin CATID’leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Ve proje sistemlerini genişletmek için kullanılan nesneler Için CATIDs 'leri listeler [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl Yapılır: Projeye Özgü Düzenleyicileri Açma](../../extensibility/how-to-open-project-specific-editors.md)  
 Bir proje için belirli bir düzenleyiciye bağlanacak bir öğe doğası gereği açmak için adım adım yönergeler sağlar.  
  
 [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)  
 Standart bir düzenleyiciyi açmak için adım adım yönergeler sağlar.  
  
 [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)  
 Project Subtype kavramsal konularına bağlantılar sağlar. Proje alt türleri mevcut [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ve [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projeleri genişletmelidir.  
  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Yeni proje türlerinin nasıl tasarlanabileceği hakkında bilgi sunan ek konuların bağlantılarını sağlar.
