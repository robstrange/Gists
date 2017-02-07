(.es(index='dccrime',timefield='ReportDate'),.es(index='weather',timefield='Date',metric='sum:MeanTemp')).mvavg(10).range(0,100)

.es(index='dccrime',timefield='ReportDate').derivative().mvavg(10)
