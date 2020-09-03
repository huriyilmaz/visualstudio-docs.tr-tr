---
title: Menüleri ve komutları genişletme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c344d996c70012ef1516fa2bebe52394739bea35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85768580"
---
# <a name="extend-menus-and-commands"></a>Menüleri ve komutları Genişlet
Komutlar, Visual Studio 'ya eylemler ve işlemler eklemenize olanak sağlar. Çoğu durumda, komutlar menülerde veya araç çubuklarında görüntülenir. VSPackage proje şablonu, çok temel bir komutun nasıl uygulanacağını gösterir. Biraz daha uzun ancak hala temel bir uygulama için bkz. [menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

 Visual Studio komutları, menüleri ve araç çubukları hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).

 Komutlar, menüler ve araç çubukları VSPackage projelerinin bir parçası olan *. vsct* dosyasında tanımlanmıştır. Visual Studio IDE ve *. vsct* dosyası hakkında, [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)hakkında bilgi edinebilirsiniz.

 Aşağıdaki konularda, farklı türlerde komutlar, menüler ve araç çubuklarının nasıl ekleneceği açıklanmaktadır.

## <a name="in-this-section"></a>Bu bölümde
- [Visual Studio menü çubuğuna bir menü ekleyin](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Üst Visual Studio menü çubuğuna bir menünün nasıl ekleneceğini açıklar.

- [Klavye kısayollarını menü öğelerine bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Bir menü öğesine klavye kısayolunun (CTRL + 3 gibi) nasıl ekleneceğini açıklar.

- [Menüye alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md) Üst menüye bir alt menü nasıl ekleneceğini açıklar.

- [Alt menüye en son kullanılan bir liste ekleme](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) En son kullanılan listenin nasıl ekleneceğini açıklar.

- Yeniden [kullanılabilir düğme grupları oluşturma](../extensibility/creating-reusable-groups-of-buttons.md) Komut öğelerinin birden çok menüye dahil edilmesini sağlamak için nasıl gruplandırılacağını açıklar.

- [Menü komutlarına simgeler ekleme](../extensibility/adding-icons-to-menu-commands.md) Hem araç çubuğunda hem de menüsünde bir komuta bir simgenin nasıl ekleneceğini açıklar.

- [Menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md) `TextChanges` Bir menü öğesinin dinamik olarak değiştirilmesini sağlamak için bayrağın kullanımını açıklar.

- [Komutun görünümünü değiştirme](../extensibility/changing-the-appearance-of-a-command.md) Bir komutun dinamik olarak nasıl etkinleştirileceğini veya devre dışı bırakılacağını açıklar.

- [Kullanıcı arabirimini güncelleştir](../extensibility/updating-the-user-interface.md) Son değişiklikleri yansıtmak için Kullanıcı arabirimi 'nin güncelleştirilmesini nasıl zorlamayabileceğinizi açıklar.

- [Yerelleştirmek menü komutları](../extensibility/localizing-menu-commands.md) Menü komutlarının nasıl yerelleştirileceğini açıklar.
