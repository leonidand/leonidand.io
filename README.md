# leonidand.io
def investment_calculator(initial_investment, annual_interest_rate, inflation_rate, additional_investments, investment_frequency, reinvestment_periods):
    
    # расчет общего количества инвестиций
    total_investments = len(additional_investments) + 1
    
    # определение частоты инвестирования
    if investment_frequency == 'Ежемесячно':
        frequency = 12
    elif investment_frequency == 'Ежеквартально':
        frequency = 4
    elif investment_frequency == 'Ежегодно':
        frequency = 1
    
    # расчет общего количества периодов реинвестирования
    total_reinvestment_periods = reinvestment_periods * frequency
    
    # расчет общей суммы дополнительных инвестиций
    total_additional_investments = sum(additional_investments)
    
    # расчет итоговой суммы вклада
    total_investment = initial_investment * ((1 + annual_interest_rate / frequency) ** (total_investments * frequency) - 1) / (annual_interest_rate / frequency) + (total_additional_investments * ((1 + annual_interest_rate / frequency) ** (total_investments * frequency) - 1) / (annual_interest_rate / frequency)) + (total_investment * ((1 + annual_interest_rate / frequency) ** total_reinvestment_periods))
    
    # учет влияния инфляции на итоговую сумму вклада
    final_investment = total_investment / ((1 + inflation_rate / frequency) ** (total_investments * frequency))
    
    return final_investment
