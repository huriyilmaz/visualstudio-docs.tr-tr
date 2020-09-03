---
title: 'İzlenecek yol: özel bir düzenleyici oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b1b4e59e43a4a5aeb129464a34b96ef3f665e72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148864"
---
# <a name="walkthrough-creating-a-custom-editor"></a>İzlenecek Yol: Özel Düzenleyici Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage proje şablonu C++ ' da basit bir özel düzenleyici oluşturabilir.  VSPackage proje şablonu artık C# veya Visual Basic projelerini desteklememektedir. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Visual Studio paketi proje şablonu  
 Visual Studio paketi proje şablonu, C++ genişletilebilirlik klasöründeki **Yeni proje** iletişim kutusunda bulunabilir  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Visual Studio paket şablonunu kullanarak bir VSPackage oluşturmak için  
  
1. Visual Studio paket şablonuyla bir proje oluşturun.  
  
2. **Özel düzenleyici** seçeneğini belirleyin ve **İleri**' ye tıklayın. **Düzenleyici seçenekleri** sayfası görüntülenir.  
  
3. Düzenleyicinin adını **Düzenleyici adı** kutusuna yazın. **Dosya Uzantısı** kutusunda düzenleyicinizle ilişkilendirilmesini istediğiniz dosya uzantısını yazın. Düzenleyiciniz bu uzantıya sahip dosyalar için kullanılabilir. Dosya uzantısı, Windows için değil yalnızca Visual Studio için kaydedilir. Düzenleyicinizle oluşturulan yeni belgeler **için varsayılan dosya adı kutusuna varsayılan** dosya adını yazın.  
  
4. Belirttiğiniz klasörde VSPackage 'nizi oluşturmak için **son** ' a tıklayın.  
  
### <a name="to-test-your-custom-editor"></a>Özel düzenleyicinizi test etmek için  
  
1. **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Dosya**' ya tıklayın.  
  
2. **Yeni dosya** Iletişim kutusunun **yüklü şablonlar** bölmesinde dosya şablonunu ve ardından Yeni kaydettiğiniz dosya türünü seçin.  
  
3. Belgeyi görüntülemek ve düzenlemek için **Aç** ' a tıklayın.  
  
     Düzenleyici, kesme ve yapıştırmayı, bulma ve değiştirme işlemlerini ve açık ve yükleme işlemlerini destekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’lar](../extensibility/internals/vspackages.md)
