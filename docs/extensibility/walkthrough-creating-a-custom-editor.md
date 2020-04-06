---
title: 'Walkthrough: Özel Düzenleyici Oluşturma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697682"
---
# <a name="walkthrough-create-a-custom-editor"></a>Walkthrough: Özel bir düzenleyici oluşturma
VSPackage proje şablonu C++'da basit bir özel düzenleyici oluşturabilir. VSPackage proje şablonu artık C# veya Visual Basic projelerini desteklemiyor. Daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenmeyi takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="the-visual-studio-package-project-template"></a>Visual Studio Paketi proje şablonu
 Visual Studio Paketi proje şablonu **c++ Genişletilebilirlik** klasörü altında **Yeni Proje** iletişim kutusunda bulabilirsiniz.

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Visual Studio paket şablonu kullanarak bir VSPackage oluşturmak için

1. Visual Studio Package şablonuyla bir proje oluşturun.

2. Özel **Düzenleyici** seçeneğini seçin ve **İleri'yi**tıklatın. **Düzenleyici Seçenekleri** sayfası görüntülenir.

3. **DüzenleyiciAdı** kutusuna editörünüzün adını yazın. **Dosya Uzantısı** kutusuna düzenleyicinizle ilişkilendirmek istediğiniz dosya uzantısını yazın. Düzenleyiciniz bu uzantıya sahip dosyalar için kullanılabilir. Dosya uzantısı yalnızca Visual Studio için kayıtlıdır, Windows için değil. **Varsayılan Dosya Adı** kutusuna düzenleyicinizle oluşturulan yeni belgeler için varsayılan dosya adını yazın.

4. Belirlediğiniz klasörde VSPackage'ınızı oluşturmak için **Bitir'i** tıklatın.

### <a name="to-test-your-custom-editor"></a>Özel düzenleyicinizi test etmek için

1. **Dosya** menüsünde **Yeni'yi** işaret edin ve ardından **Dosya'yı**tıklatın.

2. **Yeni Dosya** iletişim kutusunun **Yüklü Şablonlar** bölmesinde, dosya şablonunu, ardından kaydettiğiniz dosya türünü seçin.

3. Belgeyi görüntülemek ve görüntülemek için **Aç'ı** tıklatın.

     Düzenleyici, kes-yapıştır, bul-değiştir ve aç ve yükle işlemlerini destekler.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
