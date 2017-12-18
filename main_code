import math
WIDTH = 20

def getLoanInfo():
    loanAmt      = float(input('Enter Loan Amount: '))
    interestRate = float(input('Enter Interest Rate: '))
    return loanAmt, interestRate    

def loanTermMenu():
    print('-' * WIDTH)
    print('Loan Report Menu: ')
    print('-' * WIDTH)
    print('1.  One Year') 
    print('2.  Two Year') 
    print('3.  Three Year') 
    print('4.  Four Year') 
    print('5.  Five Year') 
    print('0.  EXIT')
    print()
    menuChoice = -9999
    menuChoice = int(input('Please Enter A Choice Above: '))
    if menuChoice == 0:
        print('EXITED')
    else:
        while menuChoice < 0 or menuChoice > 5:
            menuChoice = int(input('\nInvalid Selection\nRe-Enter Valid Selection: '))
        print('Valid Selection', menuChoice)
    monthTerm = (menuChoice * 12)
    return monthTerm

def calcPayment(monthTerm, loanAmt, interestRate):
    interestPP = ((interestRate * .1) / monthTerm)
    paymentAmt =  (interestPP * loanAmt) / (1 -  (1 + interestPP)**-monthTerm)
    return paymentAmt, interestPP
    

def displayPmtReport(paymentAmt, monthTerm, interestPP, loanAmt):
    headerFmt = ' {0:10}{1:10}{2:10}{3:10}{4:20s}'
    valueFmt  = '{0:5d}{1:12,.2f}{2:10,.2f}{3:12,.2f}{4:12,.2f}'
    print(headerFmt.format('Pmt#','PmtAmt','Int','Princ','Balance'))
    balance   = loanAmt
    for payments in range(1,monthTerm+1):
        interest  = balance * interestPP
        principle = paymentAmt - interest
        balance  -= principle
        print(valueFmt.format(payments, paymentAmt, interest, principle, balance))


def main():
    loanAmt, interestRate = getLoanInfo()
    monthTerm             = loanTermMenu()
    paymentAmt,interestPP = calcPayment(monthTerm, loanAmt, interestRate)
    displayPmtReport(paymentAmt, monthTerm, interestPP, loanAmt)
    runAgain = input("Run Again? Enter 'Y', Press any key to Exit: ").upper()
    while runAgain == 'Y':
        loanAmt, interestRate = getLoanInfo()
        monthTerm             = loanTermMenu()
        paymentAmt,interestPP = calcPayment(monthTerm, loanAmt, interestRate)
        displayPmtReport(paymentAmt, monthTerm, interestPP, loanAmt)
        runAgain = input("Run Again? Enter 'Y', Press any key to Exit: ").upper()
    else:
        print('Good Bye')
        
main()
