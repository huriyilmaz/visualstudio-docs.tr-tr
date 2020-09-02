---
title: VSPackage durumu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62980001"
---
# <a name="vspackage-state"></a>VSPackage durumu
Birçok etken, bir uygulamanın kalıcı değerler veya durumu kümesini tespit ediyor [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Projeler proje ve yapılandırma özelliklerine sahiptir.  
  
- Çözümlerin özellikleri vardır.  
  
- Kullanıcı ayarları, Belge pencerelerinin, araç pencerelerinin, yerleştirme durumunun ve klavye kısayollarının boyutunu ve konumunu belirlenir.  
  
- Uygulamalar, bir kullanıcının ayarladığı seçeneklere sahip olabilir.  
  
- Bir uygulamanın oluşturduğu nesneler kendi özelliklerine sahip olabilir.  
  
  Uygulama durumunun yönetilebilmesi için bazı yollar şunlardır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
- Proje ve çözüm Özellik sayfaları aracılığıyla.  
  
- Bir kullanıcının ayarları bir bilgisayardan diğerine taşımasını sağlayan **içeri ve dışarı aktarma ayarları Sihirbazı**aracılığıyla.  
  
- **Seçenekler** iletişim kutusunda, uygulamalarla ilgili seçenekleri içerir.  
  
- Nesneler özelliklerini kullanıma sunan **Özellikler** penceresi aracılığıyla.  
  
- Otomasyon aracılığıyla. Bir uygulama, Automation 'a sunulan VSPackage ve nesne özelliklerine erişebilir.  
  
  Uygulama durumunu temel alan uygulama durumunun kaydedilip geri yüklenmesini sağlayan çeşitli Kalıcılık mekanizmalarda bulunur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Durum kalıcılığı desteği](../misc/support-for-state-persistence.md)  
 Bir VSPackage 'ın durumunu kaydetme, geri yükleme ve sıfırlamaya yönelik yaygın stratejileri listeler.  
  
 [Seçenekler ve Seçenekler Sayfaları](../extensibility/internals/options-and-options-pages.md)  
 Genel ve özel seçenek sayfalarını tanıtır ve bunların nasıl uygulanacağını açıklar.  
  
 [Seçenekler Sayfası Oluşturma](../extensibility/creating-an-options-page.md)  
 İki seçenek sayfasının, basit bir sayfanın ve özel bir sayfanın nasıl oluşturulduğunu açıklar.  
  
 [Ayarlar kategorileri için destek](../misc/support-for-settings-categories.md)  
 Kullanıcı ayarlarını ve bunların nasıl oluşturulduğunu ve kalıcı olduğunu açıklar.  
  
 [Ayarlar Kategorisi Oluşturma](../extensibility/creating-a-settings-category.md)  
 Bir ayarlar kategorisinin nasıl oluşturulduğunu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve bir ayarlar dosyasından değerleri kaydetmek ve geri yüklemek için nasıl kullanılacağını açıklar.  
  
 [Özellikleri ve Özellik Penceresini Genişletme](../extensibility/extending-properties-and-the-property-window.md)  
 **Özellikler** penceresinde bir nesnenin değerinin nasıl görüntüleneceğini ve değiştirileceğini açıklar.  
  
 [Özellikleri ve Özellik Penceresini Kullanıma Sunma](../extensibility/exposing-properties-to-the-properties-window.md)  
 Bir nesnenin ortak özelliklerinin **Özellikler** penceresinde nasıl kullanılabileceğini açıklar.  
  
 [Proje ve Yapılandırma Özellikleri için Destek](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Proje ve yapılandırma özelliklerinin nasıl görüntüleneceğini ve değiştirileceğini açıklar.  
  
 [Proje Özelliklerini Alma](../extensibility/getting-project-properties.md)  
 Bir araç penceresinde proje özelliklerini görüntüleyen bir yönetilen VSPackage oluşturma adımlarında size rehberlik eder.  
  
 [Ayarlar Deposu Kullanma](../extensibility/using-the-settings-store.md)  
 Ayarlar deposu Kalıcılık mekanizmasını ve nasıl kullanılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [VSPackage’lar](../extensibility/internals/vspackages.md)  
 VSPackages oluşturmayı ve kullanmayı açıklayan konularda genel bir yönlendirme sağlar.