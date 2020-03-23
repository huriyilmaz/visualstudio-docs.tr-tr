---
title: Çeşitli dosyalar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], miscellaneous
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793500faf217c74772506b4b7394d926447ffd40
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585303"
---
# <a name="miscellaneous-files"></a>Çeşitli dosyalar

Bir proje den veya çözümden bağımsız olarak dosyalar üzerinde çalışmak için Visual Studio düzenleyicisini kullanmak isteyebilirsiniz. Açık bir çözümünüz varken, dosyaları bir çözüme veya projeye eklemeden açabilir ve değiştirebilirsiniz. Bağımsız olarak çalışmak istediğiniz dosyalara çeşitli dosyalar denir. Çeşitli dosyalar çözümlerve projeler için haricidir, yapılara dahil edilmez ve kaynak denetimi altında bir çözüme dahil edilemez.

Dosyaları bir projeden veya çözümden bağımsız olarak açmak çeşitli nedenlerle yararlıdır. Proje tabanlı bir çözüm geliştirirken görüntülemek istediğiniz bir dosyanız olabilir, ancak bu çözümün geliştirilmesinin ayrılmaz bir parçası değildir. Yaygın örnekler geliştirme notları veya yönergeleri, veritabanı şeması ve kod klipleri içerir. Ayrıca, tek başına bir dosya oluşturmak isteyebilirsiniz.

![Çözüm Projeleri](../../ide/reference/media/projects_solutions_misc.gif)

Solution Explorer, klasörün seçenekleri etkinse dosyalar için **çeşitli dosyalar** klasörü görüntüleyebilir. Seçenekler [Belgeler, Çevre, Seçenekler İletişim Kutusu'ndan](../../ide/reference/documents-environment-options-dialog-box.md)ayarlanabilir. Çeşitli bir dosyayı kapattıktan sonra, bunun için de bir seçenek etkinleştirilmedikçe, belirli bir çözüm veya projeyle ilişkilendirilmez.

**Çeşitli Dosyalar** klasörü dosyaları bağlantı olarak temsil eder. Bu klasör çözümün bir parçası olmasa da, bir çözümü açtığınızda, çözüm en son kapatıldığında açılan çeşitli dosyaların bazıları veya tümü klasörün ayarlarına bağlı olarak yeniden açılır.

> [!NOTE]
> **Çeşitli Dosyalar** klasöründe görünmeyen dosyalardan bazıları,.zip dosyaları ve .doc dosyaları gibi IDE içinde değiştiremeyeceğiniz dosyalardır. IDE, yalnızca harici bir düzenleyici aracılığıyla değiştirilebilen dosyaları izlemez.

## <a name="commands-available-in-the-ide"></a>IDE'de bulunan komutlar

Menüler, araç çubukları ve içerdikleri komutlar, açtığınız dosyanın biçimine göre değişir. Örneğin, bir metin dosyasını açtığınızda, Metin Düzenleyicisi araç çubuğu görüntülenir ve komutları kullanılabilir. Daha sonra bir XML Şema dosyasını açarsanız, XML Şema araç çubuğu görüntülenir. XML Şema'nızı düzenlerken Metin Düzenleyicisi araç çubuğunun komutları (veya araç çubuğunun kendisi) kullanılamaz. XML Şema etkin penceredir ve bu nedenle, geçerli seçim bağlamı vardır. Proje dosyası ile çeşitli bir dosya arasında geçiş yaptığınızda, projeyle ilgili tüm komutlar kaybolur ve yalnızca çeşitli dosyayla doğrudan ilişkili olanlar görüntülenir.

## <a name="folder-display-options"></a>Klasör görüntüleme seçenekleri

**Çeşitli Dosyalar** klasörü için ekran seçeneklerini, herhangi bir çeşitli dosya açmamış olsanız bile klasörün görünmesi için ayarlayabilirsiniz. Çözüm dosyası, çeşitli dosyaların listesini kalıcı olarak yönetmez. Kullanıcı başına, en son kullanılan (MRU) dosya listesini hatırlamasını sağlayan isteğe bağlı bir özellik kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Projeler ve Çözümler](../../ide/solutions-and-projects-in-visual-studio.md)
- [Belgeler, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/documents-environment-options-dialog-box.md)
