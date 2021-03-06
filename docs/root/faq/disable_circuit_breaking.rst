Is there a way to disable circuit breaking?
===========================================

Envoy comes with :ref:`certain defaults <envoy_api_msg_cluster.CircuitBreakers.Thresholds>`
for each kind of circuit breaking. Currently, there isn't a switch to turn
circuit breaking off completely; however, you could achieve a similar behavior
by setting these thresholds very high, for example, to `std::numeric_limits<uint32_t>::max()`.

Following is a sample configuration that tries to effectively disable all kinds
of circuit breaking by setting the thresholds to a value of `1000000000`.

.. code-block:: yaml

  circuit_breakers:
    thresholds:
      priority: HIGH
      max_connections: 1000000000
      max_pending_requests: 1000000000
      max_requests: 1000000000
      max_retries: 1000000000
