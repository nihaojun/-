# -using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp10
{
    class Program
    {
        static void Main(string[] args)
        {
            Calculate calculator = new Calculate();
            Console.Write("计算器\n请输入一个整数：");
            try
            {
                calculator.Num1 = int.Parse(Console.ReadLine());
            }
            catch
            {
                Console.WriteLine("输入的字符有误，请输入整数！");
                Console.ReadLine();
                return;
            }
            Console.Write("请输入操作符：");
            try
            {
                calculator.Operator = char.Parse(Console.ReadLine());
            }
            catch
            {
                Console.WriteLine("输入非法");
                Console.ReadLine();
                return;
            }
            Console.Write("请输入一个整数：");
            try
            {
                calculator.Num2 = int.Parse(Console.ReadLine());
            }
            catch
            {
                Console.WriteLine("输入的字符有误，请输入整数！");
                Console.ReadLine();
                return;
            }
            Console.WriteLine("结果是：{0}", calculator.Calculator());
            int _value;
            Console.Write("请随机输入一个整数：");
            try
            {
                _value = int.Parse(Console.ReadLine());
            }
            catch
            {
                Console.WriteLine("输入的字符有误，请输入整数！");
                Console.ReadLine();
                return;
            }
            Console.WriteLine("结果与输入的数{0}{1}!!!", _value, calculator.Equals(_value) ? "相等" : "不相等");
            Console.ReadLine();
        }
    }

    class Calculate
    {
        readonly char[] _opera = { '+', '-', '*', '/' };
        private int _number1, _number2;
        private char _operator;

        public int Num1
        {
            set
            {
                _number1 = value;
            }
            get
            {
                return _number1;
            }
        }

        public int Num2
        {
            set
            {
                _number2 = value;
            }
            get
            {
                return _number2;
            }
        }

        public char Operator
        {
            set
            {
                bool isOpera = false;
                foreach (char Opera in _opera)
                    if (Opera == value)
                        isOpera = true;
                if (isOpera)
                    _operator = value;
                else throw new Exception("ISNOTOPERATOR");//抛出不是操作符
            }
            get
            {
                return _operator;
            }
        }
        public int Calculator()
        {
            switch(Operator)
            {
                case '+': return Num1 + Num2;
                case '-': return Num1 - Num2;
                case '*': return Num1 * Num2;
                case '/': return Num1 / Num2;
                default: return int.MaxValue;
            }
        }

        public bool Equals(int Number)
        {
            if (Calculator() == Number)
                return true;
            else return false;
        }

    }
}
