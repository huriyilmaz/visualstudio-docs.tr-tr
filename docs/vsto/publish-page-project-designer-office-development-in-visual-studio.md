---
title: Yayımlama Sayfası, Project Tasarımcısı (Office geliştirme)
description: Visual Studio'da Project Tasarımcısı'nın Yayımla sayfasının dağıtım özelliklerini yapılandırmak için nasıl kullan olduğunu öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7e375133788c40184d63a696f684f58bde1d2d55
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082783"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Yayımlama Sayfası, Project Tasarımcısı (Office geliştirme Visual Studio)
  Dağıtım **özelliklerini** yapılandırmak **için Project Tasarımcısı'nın** Yayımla sayfası kullanılır.

 Bu sayfaya erişmek için, Çözüm Gezgini'de projeyi seçin ve Project **menüsünde** *ProjeAdı Özellikleri'ne* **tıklayın.** Yayımla **sayfası** görüntülenmezse Yayımla **sekmesini** seçin.

> [!NOTE]
> Yayımlama konumunu Yayımlama Sihirbazı'nda da **ayarlayabilirsiniz.** Daha fazla bilgi için, [bkz. How to: Publish an Office by using ClickOnce.](/previous-versions/bb386095(v=vs.110))

## <a name="uielement-list"></a>UIElement listesi
 **Klasör Konumu Yayımlama (web sitesi, ftp sunucusu veya dosya yolu)** Gerekli.

 Yayımlama klasörü konumu, derlemedeki Visual Studio, derlemeler ve diğer dosyalar gibi çözüm dosyalarını kopyalayacak dizinidir. Bu dizine yazma erişiminiz olmalıdır.

 Seçenekler arasında yerel bilgisayar, UNC dosya paylaşımı veya HTTP/HTTPS web sitesi yer almaktadır. Yol yerel (*c:\foldername\publishfolder),* göreli *\\ (* yayımlama ) veya tam konum (*\\ \servername\foldername* veya http://<em>servername/foldername</em>) olabilir.

 Varsayılan olarak, yayımlama konumu *http://localhost/projectname/* IIS yüklüyse veya *\\* IIS yüklü değilse yayımlama dizinidir.

 **Yükleme Klasörü URL'si** Isteğe bağlı.

 Yükleme klasörü URL'si, son kullanıcının özelleştirmeyi yükleyecek olduğu dizindir. Ayrıca çözümün güncelleştirmeleri denetlemesi için de bu yolu kullanır. Yol, yayımlama klasörü konumuyla aynı olabilir, ancak bu bir gereksinim değildir.

 Seçenekler arasında yerel bilgisayar, UNC dosya paylaşımı veya HTTP/HTTPS web sitesi yer almaktadır. Yol yerel (*c:\foldername\publishfolder),* göreli *\\ (* yayımlama ) veya tam konum (*\\ \servername\foldername* veya http://<em>servername/foldername</em>) olabilir. Tüm HTTP/HTTPS konumları US-ASCII karakterleriyle oluşturulmalıdır. Unicode karakterler desteklenmiyor.

 Yükleme yolu ayarlanırsa, özelleştirme dosyalarının kullanıcıların özelleştirmeyi yüklemesi için bu konumda olması gerekir. Konumun yalnızca son dağıtım konumunu biliyorsanız ayarlanmış olması gerekir.

 Yükleme dosyaları belgeye veya Kurulum programına göre bir konumda yer aldısa (cd seçeneği gibi) bu kutuyu boş bırakın.

 Bu değer daha sonra bir yönetici tarafından atanabilir. Daha fazla bilgi için, [bkz. How to: Change the installation path of an Office çözüm](/previous-versions/bb608626(v=vs.110)).

 **Önkoşullar** Önkoşullar Kurulum programına dahil olabilir veya yükleme sırasında isteğe bağlı olarak indirilebilir.

- **Bileşen satıcısının web sitesinden önkoşulları indirme:** Bu önkoşulları Microsoft'tan indirmek için bu seçeneği kullanın.

- **Önkoşulları uygulamam ile aynı konumdan indirin:** Önkoşulları yükleyicinize paketi için bu seçeneği kullanın. Kurulum programı ile önkoşul dosyalarının dahil olması, çözümün boyutunu artırır.

- **Önkoşulları** şu konumdan indirin: Önkoşulları bir web sayfasında veya ağ paylaşımında başka bir Kurulum programı olarak son kullanıcıların kullanımına ayrı olarak yapmak için bu seçeneği kullanın.

  **Güncelleştirmeler** Güncelleştirme aralığı, çözümün güncelleştirmeleri ne sıklıkta kontrol eder olduğunu belirler. Varsayılan değer yedi günde bir kontrol etmektir.

  Belge düzeyinde bir özelleştirme veya eklenti yüklendiğinde VSTO güncelleştirmelerin denetlendiğinde güncelleştirmeler güncelleştirilebilir ancak başlangıç performansı etkilenecektir.

  Cd veya çıkarılabilir sürücü kullanarak dağıtıyorsanız, bunu Hiçbir zaman güncelleştirmeleri **denetleme olarak ayarlayın.**

  **Seçenekler (Açıklama)** Aşağıdaki özellikler için yayımlama seçenekleri ayar olabilir:

- Yayımlama dili: Çözüm için Office.

- Publisher adı: Program **Ekle/Kaldır** veya Programlar ve Özellikler'de görünen **şirket veya geliştirici adı.**

- Ürün adı: program çözümünün Office/Kaldır veya Programlar ve **Özellikler'de** **göründüğü şekilde adı.**

- Destek URL'si: Son kullanıcıların çözüm için teknik desteğe başvur Office konumu.

  **Seçenekler (Office ayarları)** Aşağıdaki özellikler için yayımlama seçenekleri ayar olabilir:

- Çözüm adı: Çözüm Office uygulamanın içinde göründüğü Office adı.

- Açıklama: Office uygulamanın içinde göründüğü şekilde Office açıklaması.

- VSTO Eklenti Yükleme Davranışı.

  - Başlangıçta Yükle: Uygulama başlatıldığında VSTO eklentinin yük Office belirtir.

  - isteğe bağlı yükle: VSTO gerektirdiğinde, örneğin bir kullanıcı eklenti eklentisinde işlev kullanan bir kullanıcı arabirimi öğesine tıkladığında eklentinin VSTO belirtir.

  **Yayımlama dili** Bu seçenek, uygulamanın Microsoft Yazılımı Lisans Koşulları ayarlar ve önkoşullar listesinde dil paketlerini içerir. Özelleştirmenin dilini etkilemez. Kurulum programı'nın dili, uygulamanın yüklü dil Visual Studio.

  Yayımlama dilini değiştirme hakkında daha fazla **bilgi için,** bkz. Nasıl 2011' de bir uygulamanın [yayımlama ClickOnce değiştirme.](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)

  **Yayımlama sürümü** Özelleştirme için sürüm numarasını ayarlar. Sürüm numarası değiştir geldiğinde, uygulama bir güncelleştirme olarak yayımlanır. Daha önce yayımlanan sürümün üzerine yazmasını önlemek için derleme işlemi sırasında her sürüm için yeni bir klasör oluşturulur. Yayımlama sürümünün her bölümü (**Ana,** **İkincil**, **Derleme**, **Düzeltme**) en fazla beş basamak içerebilir.

  **Her sürümde düzeltmeyi otomatik olarak artırma** Isteğe bağlı. Seçildiğinde (varsayılan), sürüm **numarasının** Düzeltme bölümü, özelleştirme her yayım olduğunda bir artırılır. Bu, özelleştirmenin güncelleştirme olarak yayımlanır.

  **Şimdi Yayımla** Geçerli ayarları kullanarak uygulamayı yayımlar. Yayımlama **Sihirbazı'nda Son** düğmesine **eşdeğerdir.**

## <a name="see-also"></a>Ayrıca bkz.

- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Office kullanarak bir çözüm ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Office için çözüm önkoşulları](/previous-versions/bb608617(v=vs.110))