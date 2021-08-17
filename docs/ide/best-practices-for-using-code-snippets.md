---
title: Kod Parçacıkları İçin En İyi Uygulamalar
description: Kod parçacıkları, kod parçacığının amacı ve bunları uygulamanıza en uygun şekilde kullanmanın en iyi nasıl olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5606c09063dc72181a1011b503c745ed87c0bc47
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109649"
---
# <a name="best-practices-for-using-code-snippets"></a>Kod parçacıklarını kullanmaya yönelik en iyi yöntemler

Bir kod parçacığındaki kod, bir şey yapmak için yalnızca en temel yolu gösterir. Çoğu uygulama için kodun uygulamaya uyacak şekilde değiştirilmiş olması gerekir.

## <a name="handling-exceptions"></a>Özel durum işleme

Genellikle, kod parçacığı Deneyin... Catch blokları tüm özel durumları yakalar ve yeniden oluşturur. Bu, projeniz için doğru seçim olabilir. Her özel durum için yanıt vermenin çeşitli yolları vardır. Örnekler için [bkz. Nasıl: try/catch (C#) kullanarak](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) özel durum işleme ve [Deneyin... Yakalamak... Finally deyimi (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Dosya konumları

Dosya konumlarını uygulamanıza uyarlarken, aşağıdakiler hakkında düşünmeniz gerekir:

- Erişilebilir bir konum bulma. Kullanıcıların bilgisayarın Program Dosyaları *klasörüne* erişimi olabilir, bu nedenle dosyaları uygulama dosyalarıyla depolamak çalışmayabilirsiniz.

- Güvenli bir konum bulma. Dosyaları kök klasörde (*C: \\*) depolamak güvenli değildir. Uygulama verileri için Uygulama Verileri *klasörünü öneririz.* Uygulama, bireysel kullanıcı verileri için Belgeler klasöründeki her kullanıcı için bir *dosya* oluşturabilir.

- Geçerli bir dosya adı kullanma. Geçersiz dosya <xref:System.Windows.Forms.OpenFileDialog> adlarının <xref:System.Windows.Forms.SaveFileDialog> olasılığını azaltmak için ve denetimlerini kullanabilirsiniz. Kullanıcının bir dosyayı seçme zamanı ile kodunuzun dosyayı işleme zamanı arasında dosyanın silinebilir olduğunu lütfen farkında olun. Ayrıca, kullanıcının dosyaya yazma izinleri de yok olabilir.

## <a name="security"></a>Güvenlik

Bir kod parçacığının ne kadar güvenli olduğu, kaynak kodda nerede kullanılana ve kodda yer alan kodda nasıl değiştirildiğinden bağlıdır. Aşağıdaki listede dikkate alınacak alanlardan birkaçı yer alıyor.

- Dosya ve veritabanı erişimi

- Kod erişimi güvenliği

- Kaynakları koruma (olay günlükleri, kayıt defteri gibi)

- Gizli dizileri depolama

- Girişleri doğrulama

- Betik teknolojilerine veri geçirme

Daha fazla bilgi için bkz. [Uygulamaların güvenliğini sağlama.](../ide/securing-applications.md)

## <a name="downloaded-code-snippets"></a>İndirilen kod parçacıkları

Visual Studio intelliSense kod parçacıkları kendi başına bir güvenlik tehlikesinde değildir. Ancak, uygulamanıza güvenlik riskleri oluşturabilirler. İnternet'den indirilen kod parçacıkları, diğer indirilen içerikler gibi çok dikkatli bir şekilde işilmelidir.

- Kod parçacıklarını yalnızca güvenen sitelerden indirin ve güncel virüs yazılımlarını kullanın.

- İndirilen tüm kod parçacığı dosyalarını Not Defteri xml düzenleyicisinde Visual Studio ve yüklemeden önce dikkatle gözden geçirebilirsiniz. Aşağıdaki sorunları bakın:

  - Kod parçacığı kodu yürütülürse sisteminize zarar verebilir. Çalıştırmadan önce kaynak kodu dikkatle okuyun.

  - Kod parçacığı dosyasının Yardım URL'si bloğu, kötü amaçlı bir betik dosyası yürüten veya rahatsız edici bir web sitesi görüntüen URL'ler içerebilir.

  - Kod parçacığı, projenize sessizce eklenen başvurular içerebilir ve sisteminizin herhangi bir yerinden yüklenebilir. Bu başvurular, kod parçacığını indirdiğiniz bilgisayarınıza indirilmiş olabilir. Kod parçacığı daha sonra, başvuruda kötü amaçlı kod yürüten bir yönteme çağrıda olabilir. Kendinizi böyle bir saldırıya karşı korumak için kod parçacığı dosyasının İçeri Aktarmalar ve Başvurular bloklarını gözden geçirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic IntelliSense kod parçacıkları](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Uygulamaların güvenliğini sağlama](../ide/securing-applications.md)
- [Kod parçacıkları](../ide/code-snippets.md)
