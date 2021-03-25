---
title: 'İzlenecek yol: özel bir düzenleyici oluşturma | Microsoft Docs'
description: VSPackage proje şablonunun, bu yönergeyi kullanarak C++ ' da basit özel bir düzenleyici nasıl oluşturabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79adcf719091619fe4c4eb62b1fe89ba3da388f5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062024"
---
# <a name="walkthrough-create-a-custom-editor"></a>İzlenecek yol: özel bir düzenleyici oluşturma
VSPackage proje şablonu C++ ' da basit bir özel düzenleyici oluşturabilir. VSPackage proje şablonu artık C# veya Visual Basic projelerini desteklememektedir. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Visual Studio paketi proje şablonu
 Visual Studio Package proje şablonunu, **C++ genişletilebilirlik** klasörü altındaki **Yeni proje** iletişim kutusunda bulabilirsiniz.

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Visual Studio paket şablonunu kullanarak bir VSPackage oluşturmak için

1. Visual Studio paket şablonuyla bir proje oluşturun.

2. **Özel düzenleyici** seçeneğini belirleyin ve **İleri**' ye tıklayın. **Düzenleyici seçenekleri** sayfası görüntülenir.

3. Düzenleyicinin adını **Düzenleyici adı** kutusuna yazın. **Dosya Uzantısı** kutusunda düzenleyicinizle ilişkilendirilmesini istediğiniz dosya uzantısını yazın. Düzenleyiciniz bu uzantıya sahip dosyalar için kullanılabilir. Dosya uzantısı, Windows için değil yalnızca Visual Studio için kaydedilir. Düzenleyicinizle oluşturulan yeni belgeler **için varsayılan dosya adı kutusuna varsayılan** dosya adını yazın.

4. Belirttiğiniz klasörde VSPackage 'nizi oluşturmak için **son** ' a tıklayın.

### <a name="to-test-your-custom-editor"></a>Özel düzenleyicinizi test etmek için

1. **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Dosya**' ya tıklayın.

2. **Yeni dosya** Iletişim kutusunun **yüklü şablonlar** bölmesinde dosya şablonu ' nu ve ardından kaydettiğiniz dosya türünü seçin.

3. Belgeyi görüntülemek ve düzenlemek için **Aç** ' a tıklayın.

     Düzenleyici, kesme ve yapıştırmayı, bulma ve değiştirme işlemlerini ve açık ve yükleme işlemlerini destekler.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
