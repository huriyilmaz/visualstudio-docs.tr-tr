---
title: 'Kılavuz: Özel Düzenleyici Oluşturma | Microsoft Docs'
description: Bu kılavuzda, VSPackage proje şablonunun C++ içinde basit bir özel düzenleyici oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8b2c06afa6391ea516d29e244ee869e21272bf0d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157936"
---
# <a name="walkthrough-create-a-custom-editor"></a>Adım adım kılavuz: Özel düzenleyici oluşturma
VSPackage proje şablonu C++ içinde basit bir özel düzenleyici oluşturabilir. VSPackage proje şablonu artık C# veya Visual Basic desteklemez. Daha fazla bilgi için [bkz. Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu takip etmek için Visual Studio SDK'sı yüklemeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="the-visual-studio-package-project-template"></a>Visual Studio Paketi proje şablonu
 Visual Studio Paketi proje şablonunu C++ **Genişletilebilirlik** Project Yeni Uygulama **iletişim kutusunda** bulabilirsiniz.

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Visual Studio şablon kullanarak VSPackage oluşturmak için

1. Visual Studio Paketi şablonuyla bir proje oluşturun.

2. Özel Düzenleyici **seçeneğini belirleyin ve** Ardından'ya **tıklayın.** Düzenleyici **Seçenekleri** sayfası görüntülenir.

3. Düzenleyici Adı kutusuna düzenleyicinizin **adını** yazın. Düzenleyiciniz ile ilişkilendirilen dosya uzantısını Dosya Uzantısı **kutusuna** yazın. Düzenleyiciniz bu uzantıya sahip dosyalar için kullanılabilir. Dosya uzantısı yalnızca Visual Studio için kaydedilir, yalnızca Windows. Düzenleyiciniz ile oluşturulan yeni belgelerin varsayılan dosya adını Varsayılan **Dosya Adı kutusuna** yazın.

4. VsPackage'nızı belirttiğiniz klasörde oluşturmak için Son'a tıklayın. 

### <a name="to-test-your-custom-editor"></a>Özel düzenleyicinizi test etmek için

1. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** Ardından Dosya'ya **tıklayın.**

2. Yeni **Dosya iletişim kutusunun** Yüklü Şablonlar **bölmesinde,** dosya şablonunu ve ardından kayıtlı dosya türünü seçin.

3. Belgeyi **görüntülemek** ve düzenlemek için Aç'a tıklayın.

     Düzenleyici, kesme ve yapıştırma, bul ve değiştir ve açma ve yükleme işlemlerini destekler.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
