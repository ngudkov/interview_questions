Необходимо сделать рефакторинг 
=================================


``` python
from project.strategies import container as strategies_container
from project.schemas import ScorePlayload
from altron.http import response, abort
from flask import request
@app.route('/strategies/<strategy>')
def get_strategy(strategy):
    if strategies_container.has(strategy):
        strategy = strategies_container.get(strategy)
    else:
        error = 'Неизвестное имя стратегии: ' + strategy
        abort.not_found(error) # raise 404

    try:
        payload = request.get_json(force=True, selint=True)
    except BaseException:
        error = 'payload get error'
        abort.not_found(error)  # raise 404

    if ScorePlayload().is_valid(payload):
        pass
    else:
        msg = 'Input payload validation failed'
        return response.bad_request(msg, data=payload)

    score = strategy.get_score(payload)

    return response.ok(data=score.normalize().to_dict())

@app.route('/strategies/<strategy>', methods=['DELETE'])
def post_strategy(strategy):
    if strategies_container.has(strategy):
        strategy = strategies_container.get(strategy)
    else:
        error = 'Неизвестное имя стратегии: ' + strategy
        abort.not_found(error) # raise 404

    strategies_container.remove(strategy)

    return response.ok()
 ```