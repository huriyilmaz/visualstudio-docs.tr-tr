---
title: Başlarken VSIX şablon Project ile | Microsoft Docs
description: Uzantı oluşturmak veya var olan bir uzantıyı dağıtım için Project VSIX şablonlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d73294c35e71e8684be2f4fbeca98e517385eedd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087112"
---
# <a name="get-started-with-the-vsix-project-template"></a>Kullanmaya başlayın VSIX Project oluşturma

Uzantı oluşturmak veya var olan bir uzantıyı Project için VSIX uygulama şablonunu kullanabilirsiniz. VSIX Project şablonu hem Visual Basic hem de Visual C# sürümlerine sahip ve Visual Studio SDK'sı kapsamında yüklenir.

 VSIX Project şablonu, yalnızca uzantı ve birlikte ait olduğu varlıklar hakkında bilgi içeren *source.extension.vsixmanifest* dosyasından oluşur.

 VSIX proje şablonunu bulmak için Visual Studio SDK'sı yüklemeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>VSIX Project şablonu kullanarak Özel Project Dağıtma

 Aşağıdaki adımlar VSIX projesini kullanarak diğer geliştiricilerle paylaşabilirsiniz veya Visual Studio Gallery'ye yükleyen bir proje şablonunu paketleyebilirsiniz.

1. Proje şablonu oluşturun.

    1. Şablon oluşturularak projesini açın. Bu proje herhangi bir proje türünde olabilir.

    2. Şablon **Project** Dışarı Aktar'a **tıklayın.** Sihirbazın adımlarını tamamlayın.

         *%USERPROFILE%\My Documents\Visual Studio {version}\My Exported Templates \\* içinde bir.zipdosyası oluşturulur. 

2. Boş bir VSIX projesi oluşturun.

     Dosya Yeni  >  **Dosya'Project.**  >   Arama kutusuna "vsix" yazın ve VSIX'in **C#** **veya Visual Basic** **sürümünü Project.**

3. .zip *dosyasını* projeye ekleyin. Copy to **Output Directory özelliğini** olarak `Copy Always` ayarlayın.

4. Bu **Çözüm Gezgini,** *source.extension.vsixmanifest* dosyasına çift tıklar ve **vsIX Bildirim Tasarımcısı'nda** açın ve aşağıdaki değişiklikleri yapın:

    - Ürün Adı **alanını My** Project Template **olarak ayarlayın.**

    - Ürün Kimliği **alanını** **MyProjectTemplate - 1 olarak ayarlayın.**

    - Yazar **alanını** **Fabrikam olarak ayarlayın.**

    - Açıklama alanını **Proje** **şablonum olarak ayarlayın.**

    - Varlıklar **bölümünde** bir **Microsoft.VisualStudio.ProjectTemplate** türü ekleyin ve yolunu.zip *ayarlayın.*

5. *source.extension.vsixmanifest dosyasını kaydedin ve* kapatın.

6. Projeyi derleyin.

7. Çıkış dizininde *.vsix dosyasına çift* tıklayın.

8. Bir **VSIX Yükleyicisi** ileti kutusu görüntülenir. Uzantıyı yüklemek için yönergeleri izleyin.

9. Dosyayı Visual Studio sonra yeniden açın.

::: moniker range="vs-2017"

10. Uzantılar **ve Güncelleştirmeler'i** **(Araçlar menüsünde)** ve Şablonlar **kategorisini** seçin. Kullanılabilir uzantılardan biri My **Project Template olabilir.**

::: moniker-end

::: moniker range=">=vs-2019"

10. Uzantıları **Yönet'i** seçin **(Uzantılar** menüsünde) ve Şablonlar **kategorisini** seçin. Kullanılabilir uzantılardan biri My **Project Template olabilir.**

::: moniker-end

11. Yeni proje şablonu, özgün proje **şablonuyla Project** yeni proje şablonu iletişim kutusunda görünür. Örneğin, bir Visual Basic konsol **uygulamasından VB Console** adlı bir şablon oluşturduysanız, **VB Konsolu,** Visual Basic Konsol Uygulaması **şablonuyla aynı bölmede** görünür.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Yeni Uygulama İletişim Kutusunda şablonun konumunu Project için

1. Şablon klasörleri *{Visual Studio Yükleme Yolu}\Common7\IDE\ProjectTemplates* ve *{Visual Studio Yükleme Yolu}\Common7\IDE\ItemTemplates* dizinleri içinde bulunur. Yeni Klasör iletişim kutusundaki üst düzey **bölümlerin Project,** şablon klasörlerinin adları ile tam olarak eşleşmez. Bunlar farklı ise şablon klasörünün adını kullanın.

    *.vsix dosya uzantısını*.zip *ve* ardından dosyasını açın.

2. Şablonun görünmesi gereken Yeni Klasör iletişim kutusunun bölümüyle **Project** yeni bir klasör oluşturun.

3. Şablon bir alt bölüm içinde görünecekse, aynı adla bir alt klasör oluşturun.

4. Şablon dosyasını *.zip* klasörüne taşıma.

5. Dosya *uzantısını.zip* *.vsix olarak değiştirme.*

6. VSIX bildirimini açın.

7. VSIX bildiriminde şablonun **Varlık** yolunu, şablon dosyasını içeren dizin ağacının köküne yollayacak şekilde güncelleştirin. Örneğin, şablon *\CSharp\Windows* içinde ise, başvuru *\CSharp'a işaret etmek gerekir.*
