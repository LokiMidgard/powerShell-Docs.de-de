---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Erstellen eines benutzerdefinierten Eingabefelds
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 94172102fb81a9b31b7e84188f3e60a372e9cba2
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="24f76-103">Erstellen eines benutzerdefinierten Eingabefelds</span><span class="sxs-lookup"><span data-stu-id="24f76-103">Creating a Custom Input Box</span></span>
<span data-ttu-id="24f76-104">Schreiben Sie ein benutzerdefiniertes graphisches Eingabefeld mit Microsoft .NET Framework-Formularerstellungsfunktionen in Windows PowerShell 3.0 und späteren Versionen.</span><span class="sxs-lookup"><span data-stu-id="24f76-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="24f76-105">Erstellen Sie eine benutzerdefiniertes, graphisches Eingabefeld</span><span class="sxs-lookup"><span data-stu-id="24f76-105">Create a custom, graphical input box</span></span>
<span data-ttu-id="24f76-106">Kopieren und fügen Sie Folgendes in Windows PowerShell ISE ein, und speichern Sie es als Windows PowerShell-Skript (.ps1).</span><span class="sxs-lookup"><span data-stu-id="24f76-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label) 

$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox) 

$form.Topmost = $True

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

<span data-ttu-id="24f76-107">Das Skript beginnt mit dem Laden von zwei .NET Framework-Klassen: **System.Drawing** und **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="24f76-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="24f76-108">Sie starten daraufhin eine neue Instanz der .NET Framework-Klasse **System.Windows.Forms.Form**, die ein leeres Formular oder Fenster bereitstellt, zu dem Sie Steuerelemente hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="24f76-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="24f76-109">Nachdem Sie eine Instanz der Formularklasse erstellt haben, ordnen Sie drei Eigenschaften dieser Klasse Werte zu.</span><span class="sxs-lookup"><span data-stu-id="24f76-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="24f76-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="24f76-110">**Text.**</span></span> <span data-ttu-id="24f76-111">Dies wird der Titel des Fensters.</span><span class="sxs-lookup"><span data-stu-id="24f76-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="24f76-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="24f76-112">**Size.**</span></span> <span data-ttu-id="24f76-113">Dies ist die Größe des Formulars, in Pixeln.</span><span class="sxs-lookup"><span data-stu-id="24f76-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="24f76-114">Das vorhergehende Skript erstellt ein Formular, das 300 Pixel breit und 200 Pixel hoch ist.</span><span class="sxs-lookup"><span data-stu-id="24f76-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="24f76-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="24f76-115">**StartingPosition.**</span></span> <span data-ttu-id="24f76-116">Für diese optionale Eigenschaft ist im Skript oben **CenterScreen** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="24f76-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="24f76-117">Wenn Sie diese Eigenschaft nicht hinzufügen, wählt Windows eine Stelle aus, wenn das Formular geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="24f76-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="24f76-118">Durch Festlegen der **StartingPosition** auf **CenterScreen** wird das Formular automatisch bei jedem Laden in der Mitte des Bildschirms angezeigt.</span><span class="sxs-lookup"><span data-stu-id="24f76-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="24f76-119">Als Nächstes erstellen Sie eine Schaltfläche **OK** für Ihr Formular.</span><span class="sxs-lookup"><span data-stu-id="24f76-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="24f76-120">Legen Sie die Größe und das Verhalten der Schaltfläche **OK** fest.</span><span class="sxs-lookup"><span data-stu-id="24f76-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="24f76-121">In diesem Beispiel befindet sich die Schaltfläche 120 Pixel vom oberen Formularrand und 75 Pixel vom linken Rand entfernt.</span><span class="sxs-lookup"><span data-stu-id="24f76-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="24f76-122">Die Schaltflächenhöhe beträgt 23 Pixel und die Schaltflächenlänge 75 Pixel.</span><span class="sxs-lookup"><span data-stu-id="24f76-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="24f76-123">Das Skript verwendet vordefinierte Windows-Formulartypen zur Bestimmung des Schaltflächenverhaltens.</span><span class="sxs-lookup"><span data-stu-id="24f76-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="24f76-124">In entsprechender Weise erstellen Sie eine Schaltfläche **Abbrechen**.</span><span class="sxs-lookup"><span data-stu-id="24f76-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="24f76-125">Die **Abbrechen**-Schaltfläche ist 120 Pixel vom oberen und 150 Pixel vom linken Rand des Fensters entfernt.</span><span class="sxs-lookup"><span data-stu-id="24f76-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="24f76-126">Als nächstes stellen Sie einen Beschriftungstext in Ihrem Fenster bereit, der die Information beschreibt, die Benutzer verwenden sollen.</span><span class="sxs-lookup"><span data-stu-id="24f76-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label)
```

<span data-ttu-id="24f76-127">Fügen Sie das Steuerelement (in diesem Fall ein Textfeld) hinzu, mit dem Benutzer die Informationen bereitstellen, die Sie in Ihrem Beschriftungstext beschrieben haben.</span><span class="sxs-lookup"><span data-stu-id="24f76-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="24f76-128">Es gibt viele weitere Steuerelemente, die Sie neben Textfeldern anwenden können. Weitere Steuerelemente finden Sie unter [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) auf MSDN.</span><span class="sxs-lookup"><span data-stu-id="24f76-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox)
```

<span data-ttu-id="24f76-129">Legen Sie die Eigenschaft **Topmost** auf **$True** fest, um zu erzwingen, dass das Fenster über anderen geöffneten Fenstern und Dialogfeldern geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="24f76-129">Set the **Topmost** property to **$True** to force the window to open atop other open windows and dialog boxes.</span></span>

```
$form.Topmost = $True
```

<span data-ttu-id="24f76-130">Fügen Sie als nächstes diese Codezeile zum Aktivieren des Formulars hinzu, und stellen Sie den Fokus auf das von Ihnen erstellte Textfeld ein.</span><span class="sxs-lookup"><span data-stu-id="24f76-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="24f76-131">Fügen Sie die folgende Codezeile hinzu, um das Formular in Windows anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="24f76-131">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="24f76-132">Abschließend weist der Code im Block **If** Windows an, was mit dem Formular geschehen soll, wenn Benutzer Test in das Textfeld eingeben und anschließend auf die Schaltfläche **OK** klicken oder die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="24f76-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="24f76-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="24f76-133">See Also</span></span>
- [<span data-ttu-id="24f76-134">Hey Scripting Guy: Warum funktionieren diese PowerShell GUI-Beispiele nicht?</span><span class="sxs-lookup"><span data-stu-id="24f76-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="24f76-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="24f76-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="24f76-136">Windows PowerShell-Tipp der Woche: Erstellen eines benutzerdefinierten Eingabefelds</span><span class="sxs-lookup"><span data-stu-id="24f76-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](http://technet.microsoft.com/library/ff730941.aspx)
