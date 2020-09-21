---
title: Yayımlama sayfası, proje Tasarımcısı (Office geliştirme)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dfa575bea4e629c7521cc7f4c5a79707462714c
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810999"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Yayımlama sayfası, proje Tasarımcısı (Visual Studio 'da Office geliştirme)
  **Proje Tasarımcısı** ' nın **Yayımla** sayfası, dağıtımın özelliklerini yapılandırmak için kullanılır.

 Bu sayfaya erişmek için **Çözüm Gezgini**' de projeyi seçin ve ardından **Proje** menüsünde *ProjectName* **Özellikler**' i seçin. **Yayımla** sayfası görüntülenmiyorsa, **Yayımla** sekmesini seçin.

> [!NOTE]
> Yayımlama **Sihirbazı**' nda yayımlama konumunu da ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce kullanarak Office çözümü yayımlama](/previous-versions/bb386095(v=vs.110)).

## <a name="uielement-list"></a>UIElement listesi
 **Yayımlama klasörü konumu (Web sitesi, FTP sunucusu veya dosya yolu)** Gerekli.

 Yayımlama klasörü konumu, Visual Studio 'Nun bildirim, derleme ve diğer dosyalar gibi çözüm dosyalarını, derlemeden kopyaladığı dizindir. Bu dizine yazma erişiminizin olması gerekir.

 Seçenekler yerel bilgisayar, UNC dosya paylaşma veya bir HTTP/HTTPS Web sitesi içerir. Yol yerel (*c:\folder\\publishfolder*), göreli (*Yayımla \\ *) veya tam bir konum (* \\ \SunucuAdı* \ KlasörAdı veya http://<em>ServerName/KlasörAdı</em>) olabilir.

 Varsayılan olarak, yayımlama konumu *http://localhost/projectname/* IIS yüklü veya IIS yüklü değilse * \\ Yayımla* dizinidir.

 **Yükleme klasörü URL 'si** Seçim.

 Yükleme klasörü URL 'SI, son kullanıcının özelleştirmeyi yükleyeceksiniz. Ayrıca, çözümün güncelleştirmeleri denetlemek için kullanacağı yoldur. Yol, yayımlama klasörü konumuyla aynı olabilir, ancak bu bir gereksinim değildir.

 Seçenekler yerel bilgisayar, UNC dosya paylaşma veya bir HTTP/HTTPS Web sitesi içerir. Yol yerel (*c:\folder\\publishfolder*), göreli (*Yayımla \\ *) veya tam bir konum (* \\ \SunucuAdı* \ KlasörAdı veya http://<em>ServerName/KlasörAdı</em>) olabilir. Tüm HTTP/HTTPS konumları US-ASCII karakterlerle oluşturulmalıdır. Unicode karakterler desteklenmez.

 Yükleme yolu ayarlandıysa, kullanıcıların özelleştirmeyi yüklemesi için bu konumda özelleştirme dosyaları olmalıdır. Konum yalnızca son dağıtım konumunu biliyorsanız ayarlanmalıdır.

 Yükleme dosyaları belge veya Kurulum programı ile ilişkili bir konumdaysa (örneğin, CD seçeneğinde), bu kutuyu boş bırakın.

 Bu değer, daha sonra bir yönetici tarafından atanabilir. Daha fazla bilgi için bkz. [nasıl yapılır: bir Office çözümünün yükleme yolunu değiştirme](/previous-versions/bb608626(v=vs.110)).

 **Önkoşullar** Önkoşullar Kurulum programına dahil edilebilir veya yükleme sırasında isteğe bağlı olarak indirilebilir.

- **Önkoşulları bileşen satıcısının Web sitesinden indir**: Bu seçeneği Microsoft 'un bu önkoşullarını indirmek için kullanın.

- **Önkoşulları Uygulamam ile aynı konumdan indir**: yükleyicinizdeki önkoşulları paketlemek için bu seçeneği kullanın. Önkoşul dosyalarını Kurulum programına dahil etmek çözümün boyutunu artırır.

- **Önkoşulları aşağıdaki konumdan indir**: önkoşulları son kullanıcılara bir Web sayfası veya ağ paylaşımındaki başka bir kurulum programı olarak ayrı kullanılabilir hale getirmek için kullanın.

  **Güncelleştirmeler** Güncelleştirme aralığı, çözümün güncelleştirmeleri ne sıklıkta denetleyeceğini belirler. Varsayılan değer her yedi günde bir denetdir.

  Her belge düzeyi özelleştirmesi veya VSTO eklentisi yüklendiğinde güncelleştirmeleri denetlemek, ancak başlangıç performansını etkiler.

  Bir CD veya çıkarılabilir sürücü kullanarak dağıtıyorsanız, bu ayarı **hiçbir şekilde güncelleştirmeleri denetmeme**olarak ayarlayın.

  **Seçenekler (Açıklama)** Aşağıdaki özellikler için yayımlama seçenekleri ayarlanabilir:

- Yayımlama dili: Office çözümünün yerel ayarı.

- Yayımcı adı: **Program Ekle/Kaldır** veya **Programlar ve Özellikler**bölümünde göründüğü gibi şirket veya geliştirici adı.

- Ürün adı: Office çözümünün **Program Ekle/Kaldır** veya **Programlar ve Özellikler**bölümünde göründüğü şekilde adı.

- Destek URL 'SI: son kullanıcıların Office çözümü için teknik desteğe başvurumu.

  **Seçenekler (Office ayarları)** Aşağıdaki özellikler için yayımlama seçenekleri ayarlanabilir:

- Çözüm adı: Office uygulamasında göründüğü haliyle Office çözümünün adı.

- Açıklama: Office çözümünün Office uygulamasında göründüğü haliyle açıklaması.

- VSTO eklentisi yükleme davranışı.

  - Başlangıçta yükle: Office uygulaması başlatıldığında VSTO eklentisinin yüklendiğini belirtir.

  - Isteğe bağlı yükleme: VSTO eklentisinin uygulama gerektirdiğinde, örneğin, bir kullanıcının VSTO eklentisinin işlevselliğini kullanan bir kullanıcı ARABIRIMI öğesine tıkladığı durumlarda, bu eklentinin yükleneceğini belirtir.

  **Yayımlama dili** Bu seçenek, Microsoft yazılımı lisans koşullarının dilini ayarlar ve Önkoşullar listesindeki dil paketlerini içerir. Özelleştirmenin dilini etkilemez. Kurulum programındaki dil, Visual Studio 'nun yüklü dilleri tarafından belirlenir.

  **Yayımlama dilini**değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce uygulaması Için yayımlama dilini değiştirme](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md).

  **Yayımlama sürümü** Özelleştirme için sürüm numarasını ayarlar. Sürüm numarası değiştirildiğinde, uygulama bir güncelleştirme olarak yayımlanır. Derleme işlemi sırasında, daha önce yayımlanan sürümün üzerine yazılmasını engellemek için her bir sürüm için yeni bir klasör oluşturulur. Yayımla sürümünün her bölümü (**ana**, **İkincil**, **derleme**, **Düzeltme**) en fazla beş basamak içerebilir.

  **Her sürümde düzeltmeyi otomatik olarak artır** Seçim. Seçildiğinde (varsayılan), özelleştirmenin her yayımlanışında sürüm numarasının **Düzeltme** bölümü bir artırılır. Bu, özelleştirmenin güncelleştirme olarak yayımlanmasına neden olur.

  **Şimdi Yayımla** Geçerli ayarları kullanarak uygulamayı yayımlar. **Yayımla sihirbazındaki** **son** düğmesine eşittir.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Dağıtım için Office çözüm önkoşulları](/previous-versions/bb608617(v=vs.110))