#pragma once

#include "ReverseForm.h"

namespace Var13 {
    using namespace System;
    using namespace System::ComponentModel;
    using namespace System::Collections;
    using namespace System::Windows::Forms;
    using namespace System::Data;
    using namespace System::Drawing;

    public ref class MyForm : public System::Windows::Forms::Form
    {
    public:
        MyForm(void)
        {
            InitializeComponent();
        }

    protected:
        ~MyForm()
        {
            if (components) delete components;
        }

    private:
        System::Windows::Forms::MenuStrip^ menuStrip1;
        System::Windows::Forms::ToolStripMenuItem^ reverseMenuItem;
        System::Windows::Forms::ToolStripMenuItem^ aboutMenuItem;
        System::Windows::Forms::ToolStripMenuItem^ exitMenuItem;
        System::ComponentModel::Container^ components;

        void InitializeComponent(void)
        {
            this->menuStrip1 = (gcnew System::Windows::Forms::MenuStrip());
            this->reverseMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
            this->aboutMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
            this->exitMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
            this->menuStrip1->SuspendLayout();
            this->SuspendLayout();
            // 
            // menuStrip1
            // 
            this->menuStrip1->ImageScalingSize = System::Drawing::Size(20, 20);
            this->menuStrip1->Items->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(3) {
                this->reverseMenuItem,
                    this->aboutMenuItem, this->exitMenuItem
            });
            this->menuStrip1->Location = System::Drawing::Point(0, 0);
            this->menuStrip1->Name = L"menuStrip1";
            this->menuStrip1->Size = System::Drawing::Size(645, 28);
            this->menuStrip1->TabIndex = 0;
            this->menuStrip1->Text = L"menuStrip1";
            // 
            // reverseMenuItem
            // 
            this->reverseMenuItem->Name = L"reverseMenuItem";
            this->reverseMenuItem->Size = System::Drawing::Size(74, 24);
            this->reverseMenuItem->Text = L"Reverse";
            this->reverseMenuItem->Click += gcnew System::EventHandler(this, &MyForm::reverseMenuItem_Click);
            // 
            // aboutMenuItem
            // 
            this->aboutMenuItem->Name = L"aboutMenuItem";
            this->aboutMenuItem->Size = System::Drawing::Size(64, 24);
            this->aboutMenuItem->Text = L"About";
            this->aboutMenuItem->Click += gcnew System::EventHandler(this, &MyForm::aboutMenuItem_Click);
            // 
            // exitMenuItem
            // 
            this->exitMenuItem->Name = L"exitMenuItem";
            this->exitMenuItem->Size = System::Drawing::Size(47, 24);
            this->exitMenuItem->Text = L"Exit";
            this->exitMenuItem->Click += gcnew System::EventHandler(this, &MyForm::exitMenuItem_Click);
            // 
            // MyForm
            // 
            this->AutoScaleDimensions = System::Drawing::SizeF(8, 16);
            this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
            this->ClientSize = System::Drawing::Size(645, 320);
            this->Controls->Add(this->menuStrip1);
            this->MainMenuStrip = this->menuStrip1;
            this->Margin = System::Windows::Forms::Padding(4, 4, 4, 4);
            this->Name = L"MyForm";
            this->Text = L"Горовенко А.С., группа ИСТ-03, вариант 13";
            this->menuStrip1->ResumeLayout(false);
            this->menuStrip1->PerformLayout();
            this->ResumeLayout(false);
            this->PerformLayout();

        }

    private:
        // Обработчик Reverse
        System::Void reverseMenuItem_Click(System::Object^ sender, System::EventArgs^ e) {
            ReverseForm^ revForm = gcnew ReverseForm();
            revForm->ShowDialog();
        }

        // Обработчик About
        System::Void aboutMenuItem_Click(System::Object^ sender, System::EventArgs^ e) {
            MessageBox::Show("Разработчик: Горовенко А.С.\nГруппа: ИСТ-03\nВариант 13",
                "О программе", MessageBoxButtons::OK, MessageBoxIcon::Information);
        }

        // Обработчик Exit
        System::Void exitMenuItem_Click(System::Object^ sender, System::EventArgs^ e) {
            if (MessageBox::Show("Вы действительно хотите выйти?", "Подтверждение",
                MessageBoxButtons::YesNo, MessageBoxIcon::Question) == System::Windows::Forms::DialogResult::Yes)
                Application::Exit();
        }
    };
}
