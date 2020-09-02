---
title: Menüleri ve komutları genişletme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83d9dc45863f1ed1b5e11c17b9e922b62b0186dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204528"
---
# <a name="extending-menus-and-commands"></a>Menüleri ve Komutları Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Komutlar, Visual Studio 'ya eylemler ve işlemler eklemenize olanak sağlar. Çoğu durumda, komutlar menülerde veya araç çubuklarında görüntülenir. VSPackage proje şablonu, çok temel bir komutun nasıl uygulanacağını gösterir. Biraz daha uzun ancak hala temel bir uygulama için bkz. [menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Visual Studio komutları, menüler ve araç çubukları hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Komutlar, menüler ve araç çubukları VSPackage projelerinin bir parçası olan. vsct dosyasında tanımlanmıştır. Visual Studio IDE ve. vsct dosyası hakkında, [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)hakkında bilgi edinebilirsiniz.  
  
 Aşağıdaki konularda, farklı türlerde komutlar, menüler ve araç çubuklarının nasıl ekleneceği açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Visual Studio Menü Çubuğuna Menü Ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Üst Visual Studio menü çubuğuna bir menünün nasıl ekleneceğini açıklar.  
  
 [Menü Öğelerine Klavye Kısayolları Bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Bir menü öğesine klavye kısayolunun (CTRL + 3 gibi) nasıl ekleneceğini açıklar.  
  
 [Bir Menüye Alt Menü Ekleme](../extensibility/adding-a-submenu-to-a-menu.md)  
 Üst menüye bir alt menü nasıl ekleneceğini açıklar.  
  
 [Bir Alt Menüye Son Kullanılanlar Listesi Ekleme](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 En son kullanılan listenin nasıl ekleneceğini açıklar.  
  
 [Yeniden Kullanılabilir Düğme Grupları Oluşturma](../extensibility/creating-reusable-groups-of-buttons.md)  
 Komut öğelerinin birden çok menüye dahil edilmesini sağlamak için nasıl gruplandırılacağını açıklar.  
  
 [Menü Komutlarına Simge Ekleme](../extensibility/adding-icons-to-menu-commands.md)  
 Hem araç çubuğunda hem de menüsünde bir komuta bir simgenin nasıl ekleneceğini açıklar.  
  
 [Bir Menü Komutunun Metnini Değiştirme](../extensibility/changing-the-text-of-a-menu-command.md)  
 `TextChanges`Bir menü öğesinin dinamik olarak değiştirilmesini sağlamak için bayrağın kullanımını açıklar.  
  
 [Bir Komutun Görünümünü Değiştirme](../extensibility/changing-the-appearance-of-a-command.md)  
 Bir komutun dinamik olarak nasıl etkinleştirileceğini veya devre dışı bırakılacağını açıklar.  
  
 [Kullanıcı Arabirimini Güncelleştirme](../extensibility/updating-the-user-interface.md)  
 Son değişiklikleri yansıtmak için Kullanıcı arabirimi 'nin güncelleştirilmesini nasıl zorlamayabileceğinizi açıklar.  
  
 [Menü Komutlarını Yerelleştirme](../extensibility/localizing-menu-commands.md)  
 Menü komutlarının nasıl yerelleştirileceğini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler
