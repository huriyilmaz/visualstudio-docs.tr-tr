---
title: Görsel C# kod parçacıkları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fb84854bd871277f680a753b28c17e3429283928
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646714"
---
# <a name="visual-c-code-snippets"></a>Visual C# Kod Parçacıkları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod parçacıkları, kodunuza hızlı bir şekilde ekleyebileceğiniz kod parçacıklarında kullanıma sunulur. Örneğin, `for` kod parçacığı boş bir `for` döngüsü oluşturur. Bazı kod parçacıkları, kod satırları seçmenize olanak tanıyan kod parçacıkları ile çevredir ve seçilen kod satırlarını içeren bir kod parçacığı seçer. Örneğin, kod satırları ' nı seçip `for` kod parçacığını etkinleştirdiğinizde, döngü bloğunda bu kod satırlarıyla bir `for` döngüsü oluşturur. Kod parçacıkları program kodunu daha hızlı, daha kolay ve daha güvenilir bir şekilde yazmayı kolaylaştırabilir.

 İmleç konumuna bir kod parçacığı ekleyebilir veya şu anda seçili olan kodun çevresine bir surround kod parçacığı ekleyebilirsiniz. Kod parçacığı eklenebilir kod **parçacığı ekleme** veya **IntelliSense** menüsündeki komutlarla **çevreleme** ya da Ctrl + k ve daha sonra X ya da Ctrl + k ve sonra sırasıyla bulunan klavye kısayolları kullanılarak çağrılır.

 Kod parçacığı Inserter, tüm kullanılabilir kod parçacıkları için kod parçacığı adını görüntüler. Kod parçacığı Inserter, kod parçacığının adını veya kod parçacığı adının bir bölümünü girebileceğiniz bir giriş iletişim kutusu da içerir. Kod parçacığı Inserter, bir kod parçacığı adına en yakın eşleşmeyi vurgular. İstediğiniz zaman TAB tuşuna basıldığında kod parçacığı eklenebilir ve şu anda seçili kod parçacığı işaretlenir. Kod Düzenleyicisi 'nde ESC yazmak veya fareye tıklamak, kod parçacığı eklemeden kod parçacığı yerleştiriciyi yok eder.

## <a name="default-code-snippets"></a>Varsayılan kod parçacıkları
 Varsayılan olarak, aşağıdaki kod parçacıkları Visual Studio 'Ya eklenmiştir.

|Ad (veya kısayol)|Açıklama|Kod parçacığı eklemek için geçerli konumlar|
|--------------------------|-----------------|---------------------------------------|
|#if|Bir [#if](https://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) yönergesi ve [#endif](https://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05) yönergesi oluşturur.|Yerdeki.|
|#region|Bir [#region](https://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) yönergesi ve [#endregion](https://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526) yönergesi oluşturur.|Yerdeki.|
|~|İçerilen sınıf için bir yıkıcı oluşturur.|Bir sınıf içinde.|
|özniteliği|@No__t_0 türetilen bir sınıf için bir bildirim oluşturur.|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|checked|[Denetlenen](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) bir blok oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|sınıf|Bir sınıf bildirimi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|'u|İçerilen sınıf için bir Oluşturucu oluşturur.|Bir sınıf içinde.|
|fiili|@No__t_0 için bir çağrı oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|do|[Do](https://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb) `while` döngüsü oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|else|[Else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|enum|Bir [sabit listesi](https://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c) bildirimi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|eşittir|@No__t_1 sınıfında tanımlanmış <xref:System.Object.Equals%2A> yöntemini geçersiz kılan bir yöntem bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|duruma|Özel durumdan türetilen bir sınıf için bildirim oluşturur (varsayılan olarak <xref:System.Exception>).|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|for|[For](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) döngüsü oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|foreach|Bir [foreach](https://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec) döngüsü oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|Öğrencilerinize|Her yinelemeden sonra döngü değişkenini azaltır bir [for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) döngüsü oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|if|[IF](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|dizinleyic|Bir Dizin Oluşturucu bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|arabirim|[Arabirim](https://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) bildirimi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|Resync|Güvenli bir şekilde olay çağıran bir blok oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|iterator|Bir yineleyici oluşturur.|Bir sınıf veya yapı içinde.|
|yinedizin|İç içe bir sınıf kullanarak "adlandırılmış" yineleyici ve Dizin Oluşturucu çifti oluşturur.|Bir sınıf veya yapı içinde.|
|lock|Bir [kilit](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|MBOX|@No__t_0 için bir çağrı oluşturur. System. Windows. Forms. dll ' ye bir başvuru eklemeniz gerekebilir.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|ad alanı|Bir [ad alanı](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) bildirimi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil).|
|Prop|[Otomatik uygulanan bir özellik](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|propfull|Get ve set erişimcilerine sahip bir özellik bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|propg|Özel bir "set" erişimcisine sahip salt okunurdur bir [Otomatik uygulanan özellik](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) oluşturur.|Bir sınıf veya yapı içinde.|
|SIM|Statik bir [](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[int](https://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52) Main yöntemi bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|struct|Bir [struct](https://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c) bildirimi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|SVM|[Statik](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[void](https://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4) Main yöntemi bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|anahtarı|Bir [anahtar](https://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|almaya|[Try-catch](https://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|tryf|[Try-finally](https://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|unchecked|[Denetlenmemiş](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) bir blok oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|unsafe|[Güvenli olmayan](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) bir blok oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|kullanma|Bir [using](https://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8) yönergesi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil).|
|while|[While](https://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59) döngüsü oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod parçacığı işlevleri](../ide/code-snippet-functions.md) [kod parçacıklarını](../ide/code-snippets.md) [nasıl yapılır: değiştirmeler şablon parametreleriyle yeni bir kod parçacığı oluşturma](https://msdn.microsoft.com/8d56d43c-097a-475b-aa85-cae1554b6338) [](../ide/template-parameters.md) [nasıl yapılır: kod parçacıkları Ile surround kullanımı](../ide/how-to-use-surround-with-code-snippets.md) [nasıl yapılır: yeniden C# düzenleme parçacıklarını geri yükleme](../ide/how-to-restore-csharp-refactoring-snippets.md)
