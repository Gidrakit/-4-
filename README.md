# -4-
My first repository on GitHub. and forth practic
procedure TForm1.Image1Click(Sender: TObject);
begin

end;

procedure TForm1.N10Click(Sender: TObject);
var
  error:boolean;
  i,int:integer;
begin
  if view then begin
    error:=false;
    if SaveDialog1.Execute then begin
      if assignFile_(f,SaveDialog1.FileName)=0 then begin
        if rewriteFile_(f)=0 then inorderstf(head,f);
      end;
      Form4.Label1.Caption:='Файл успешно записан';
      Form4.Button1.Width:=Form4.Label1.Width;
      Form4.Width:=Form4.Label1.Width+20;
      Form4.ShowModal;
      closeFile(f);
    end;
  end else begin
    Form4.Label1.Caption:='Отсутствуют данные для записи';
    Form4.Button1.Width:=Form4.Label1.Width;
    Form4.Width:=Form4.Label1.Width+20;
    Form4.ShowModal;
  end;
end;

procedure TForm1.N11Click(Sender: TObject);
begin
  if Unit1.view then begin
    Form2.Label1.Caption:='Элемент для добавления';
    Form2.Button1.Width:=Form2.Label1.Width;
    Form2.Width:=Form2.Label1.Width+20;
    Form2.Edit1.Width:=Form2.Label1.Width;
    search:=true;
    rand:=false;
    add:=false;
    delete:=false;
    swap:=false;
    Form2.ShowModal;
  end else begin
    Form4.Label1.Caption:='Отсутствует список';
    Form4.Button1.Width:=Form4.Label1.Width;
    Form4.Width:=Form4.Label1.Width+20;
    Form4.ShowModal;
  end;
end;

procedure TForm1.N14Click(Sender: TObject);
var
  str:string;
begin
  if not view then begin
    Form4.Label1.Caption:='Отсутствуют данные для вывода';
    Form4.Button1.Width:=Form4.Label1.Width;
    Form4.Width:=Form4.Label1.Width+20;
    Form4.ShowModal;
  end else begin
    Form5.Label1.Caption:='Ваши элементы: ';
    preorder(Unit1.head,str);
    Form5.Label1.Caption:=Form5.Label1.Caption+str;
    Form5.Width:=Form5.Label1.Width+15;
    Form5.ShowModal;
  end;
end;

procedure TForm1.N2Click(Sender: TObject);
begin
  Form2.Label1.Caption:='Введите элементы';
  Form2.Button1.Width:=Form2.Label1.Width;
  Form2.Width:=Form2.Label1.Width+20;
  Form2.Edit1.Width:=Form2.Label1.Width;
  rand:=false;
  add:=false;
  delete:=false;
  search:=false;
  swap:=false;
  Form2.ShowModal;
end;

procedure TForm1.N31Click(Sender: TObject);
var
  str:string;
begin
  if not view then begin
    Form4.Label1.Caption:='Отсутствуют данные для вывода';
    Form4.Button1.Width:=Form4.Label1.Width;
    Form4.Width:=Form4.Label1.Width+20;
    Form4.ShowModal;
  end else begin
    Form5.Label1.Caption:='Ваши элементы: ';
    postorder(Unit1.head,str);
    Form5.Label1.Caption:=Form5.Label1.Caption+str;
    Form5.Width:=Form5.Label1.Width+15;
    Form5.ShowModal;
  end;
end;

procedure TForm1.N3Click(Sender: TObject);
var
  i,int:integer;
  error:boolean;
begin
  error:=false;
  if OpenDialog1.Execute then begin
    if assignFile_(f,OpenDialog1.FileName)=0 then begin
      if resetFile_(f)=0 then begin
        while not eof(f) do begin
          read(f,int);
          AddToTree(head,int);
        end;
        Form4.Label1.Caption:='Файл успешно считан';
        Form4.Button1.Width:=Form4.Label1.Width;
        Form4.Width:=Form4.Label1.Width+20;
        Form4.ShowModal;
        view:=true;
      end;
    end;
    closeFile(f);
  end;
end;

procedure TForm1.N4Click(Sender: TObject);
var
  count:integer;
begin
  count:=0;
  inordercount(head,count);
  Form4.Label1.Caption:='Количество узлов: '+IntToStr(count);
  Form4.Button1.Width:=Form4.Label1.Width;
  Form4.Width:=Form4.Label1.Width+20;
  Form4.ShowModal;
end;

procedure TForm1.N6Click(Sender: TObject);
begin
  if view then begin
    DeleteTree(head);
    Form4.Label1.Caption:='Дерево удалено';
    Form4.Button1.Width:=Form4.Label1.Width;
    Form4.Width:=Form4.Label1.Width+20;
    Form4.ShowModal;
    view:=false;
  end else begin
    DeleteTree(head);
    Form4.Label1.Caption:='Дерево не найдено';
    Form4.Button1.Width:=Form4.Label1.Width;
    Form4.Width:=Form4.Label1.Width+20;
    Form4.ShowModal;
  end;
end;

procedure TForm1.N7Click(Sender: TObject);
begin
  if Unit1.view then begin
    Form2.Label1.Caption:='Элемент для удаления';
    Form2.Button1.Width:=Form2.Label1.Width;
    Form2.Width:=Form2.Label1.Width+20;
    Form2.Edit1.Width:=Form2.Label1.Width;
    delete:=true;
    Form2.ShowModal;
  end else begin
    Form4.Label1.Caption:='Отсутствует список';
    Form4.Button1.Width:=Form4.Label1.Width;
    Form4.Width:=Form4.Label1.Width+20;
    Form4.ShowModal;
  end;
end;

procedure TForm1.N9Click(Sender: TObject);
var
  str:string;
begin
  if not view then begin
    Form4.Label1.Caption:='Отсутствуют данные для вывода';
    Form4.Button1.Width:=Form4.Label1.Width;
    Form4.Width:=Form4.Label1.Width+20;
    Form4.ShowModal;
  end else begin
    Form5.Label1.Caption:='Ваши элементы: ';
    inorder(Unit1.head,str);
    Form5.Label1.Caption:=Form5.Label1.Caption+str;
    Form5.Width:=Form5.Label1.Width+15;
    Form5.ShowModal;
  end;
end;

end.
